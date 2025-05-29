```
Pcl, S, CS, T = hinfsignals(P::ExtendedStateSpace, G::LTISystem, C::LTISystem)
```

Use the extended state-space model, a plant and the found controller to extract the closed loop transfer functions.

  * `Pcl : w → z` : From input to the weighted functions
  * `S   : w → e` : From input to error
  * `CS  : w → u` : From input to control
  * `T   : w → y` : From input to output
