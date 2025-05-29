```
simulated_load(d::Dict)
```

This function gets DOE commercial reference building (CRB) load profile data     which is the same way that loads are processed to create REoptInputs.s (Scenario struct).

This function is used for the /simulated_load endpoint in the REopt API, in particular      for the webtool/UI to display loads before running REopt, but is also generally     an external way to access CRB load data without running REopt.

One particular aspect of this function specifically for the webtool/UI is the heating load      because there is just a single heating load instead of separated space heating and      domestic hot water loads.
