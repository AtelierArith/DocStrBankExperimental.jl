```
ExtendedStateSpace{TE, T} <: AbstractStateSpace{TE}
```

A type that represents the two-input, two-output system

```
z  ┌─────┐  w
◄──┤     │◄──
   │  P  │
◄──┤     │◄──
y  └─────┘  u
```

where

  * `z` denotes controlled outputs (sometimes called performance outputs)
  * `y` denotes measured outputs
  * `w` denotes external inputs, such as disturbances or references
  * `u` denotes control inputs

The call `lft(P, K)` forms the (lower) linear fractional transform 

```
z  ┌─────┐  w
◄──┤     │◄──
   │  P  │
┌──┤     │◄─┐
│y └─────┘ u│
│           │
│  ┌─────┐  │
│  │     │  │
└─►│  K  ├──┘
   │     │
   └─────┘
```

i.e., closing the lower loop around `K`.

An `ExtendedStateSpace` can be converted to a standard `StateSpace` by `ss(P)`, this will keep all inputs and outputs, effectively removing the partitioning only.

When [`feedback`](@ref) is called on this type, defaults are automatically set for the feedback indices. Other functions defined for this type include

  * [`system_mapping`](@ref)
  * [`performance_mapping`](@ref)
  * [`noise_mapping`](@ref)
  * [`lft`](@ref)
  * [`feedback`](@ref) has special overloads that sets defaults connections for `ExtendedStateSpace`.

and the following design functions expect `ExtendedStateSpace` as inputs

  * [`hinfsynthesize`](@ref)
  * [`h2synthesize`](@ref)
  * [`LQGProblem`](@ref) (also accepts other types)

A video tutorial on how to use this type is available [here](https://youtu.be/huYRrn--AKc).
