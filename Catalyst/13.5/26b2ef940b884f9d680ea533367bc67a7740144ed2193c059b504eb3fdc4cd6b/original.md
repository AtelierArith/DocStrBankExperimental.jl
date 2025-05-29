```
dependents(rx, network)
```

Given a [`Reaction`](@ref) and a [`ReactionSystem`](@ref), return a vector of the *non-constant* species and variables the reaction rate law depends on. e.g., for

`k*W, 2X + 3Y --> 5Z + W`

the returned vector would be `[W(t),X(t),Y(t)]`.

Notes:

  * Allocates
  * Does not check for dependents within any subsystems.
  * Constant species are not considered dependents since they are internally treated as parameters.
  * If the rate expression depends on a non-species state variable that will be included in the dependents, i.e. in

    ```julia
    @parameters k
    @variables t V(t)
    @species A(t) B(t) C(t)
    rx = Reaction(k*V, [A, B], [C])
    @named rs = ReactionSystem([rx], t)
    issetequal(dependents(rx, rs), [A,B,V]) == true
    ```
