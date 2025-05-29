```
AndersonAccelerator{T, BT, MT, RE} <: AbstractAccelerator
```

Accelerator object implementing Anderson Acceleration. Parameterized by:

  * T: AbstractFloat, floating-point type
  * BT: Broyden-type, i.e. Type1 or Type2
  * MT: AbstractMemory, how full memory buffers are handled
  * RE: AbstractRegularizer
