# High level architecture #

> The charger is designed based on two main assamptions
  * Charged battery is isolated from a car body. Having the charger permanently installed in an EV, no need to isolate it from the input grid
  * The charger and DC/DC converter are never used at the same time. Costly power components can be shared



> Charger may be not isolated. If a battery has lower voltage than input, the best idea is to use **Buck** converter. It's more efficient compare to transformer-based one. Switch Q1, inductor L, and diode Q2 form the converter. Switch Q2 in pair with a diode increases efficiency even more.

> ![http://pavlink-charger.googlecode.com/svn/wiki/images/BuckBlack.jpg](http://pavlink-charger.googlecode.com/svn/wiki/images/BuckBlack.jpg)

> DC/DC converter has to be isolated so a transformer-based converter is an only option. Fly-back converter is less complicated and has very wide input voltage range. L1 and Q2 together with secondary circuit L2 and D form the converter. Fly-back has an disadvantage, high voltage spikes which has to be clamped to protect elements.  Q1 and C4 are an active clamp.
> ![http://pavlink-charger.googlecode.com/svn/wiki/images/BlaybackClampBlack.jpg](http://pavlink-charger.googlecode.com/svn/wiki/images/BlaybackClampBlack.jpg)

> The two converters use same elements and can be combined together.
  * Blue is charging flow in buck converter.
  * Red is DC/DC flow in fly-back converter
  * Green is secondary current, which is DC/DC converter output

> ![http://pavlink-charger.googlecode.com/svn/wiki/images/FinalBlack_1.jpg](http://pavlink-charger.googlecode.com/svn/wiki/images/FinalBlack_1.jpg)

> The secondary voltage is also generated in charging mode because L2 is coupled with L1 and they form forward converter. Take note the direction of the L1 and L2

> ![http://pavlink-charger.googlecode.com/svn/wiki/images/ForwardBlack.jpg](http://pavlink-charger.googlecode.com/svn/wiki/images/ForwardBlack.jpg)

> Input voltage for the converter is Vin-Vbat so the secondary voltage is lower than in fly-back mode. That's why DC/DC output should not be used in charging mode but it's safe to have it connected.