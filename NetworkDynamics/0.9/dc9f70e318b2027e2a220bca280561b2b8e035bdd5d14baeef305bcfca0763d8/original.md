```
StateMask(i::AbstractArray)
StateMaks(i::Number)
```

A `StateMask` is a predefined output function. It can be used to define the output of a component model by picking from the internal state.

I.e. `g=StateMask(2:3)` in a vertex function will output the internal states 2 and 3. In many contexts, `StateMask`s can be constructed implicitly by just providing the indices, e.g. `g=1:2`.

For [`EdgeModel`](@ref) this needs to be combined with a [`Directed`](@ref), [`Symmetric`](@ref), [`AntiSymmetric`](@ref) or [`Fiducial`](@ref) coupling, e.g. `g=Fiducial(1:2, 3:4)` forwards states 1:2 to dst and states 3:4 to src.
