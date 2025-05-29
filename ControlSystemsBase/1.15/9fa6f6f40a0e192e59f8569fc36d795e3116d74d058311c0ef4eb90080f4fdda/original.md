```
S, PS, CS, T, RY, RU, RE = gangofseven(P,C,F)
```

Given transfer functions describing the Plant `P`, the controller `C` and a feed forward block `F`, computes the four transfer functions in the Gang-of-Four and the transferfunctions corresponding to the feed forward.

  * `S = 1/(1+PC)` Sensitivity function
  * `PS = P/(1+PC)`
  * `CS = C/(1+PC)`
  * `T = PC/(1+PC)` Complementary sensitivity function
  * `RY = PCF/(1+PC)`
  * `RU = CF/(1+P*C)`
  * `RE = F/(1+P*C)`
