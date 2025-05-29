```
State
```

Abstract supertype for all sampled states: `state <: State`.

# Examples

## Find all states that may be sampled

```julia-repl
julia> subtypes(State)

6-element Vector{Any}:
Bogoliubov
Coherent
Crescent
Fock
Squeezed
Thermal
```

## Create and sample a particular state (vacuum)

```julia-repl
julia> s = Fock(0)
Fock(0)
julia> wigner(s,100)
┌ Warning: Fock state sampling for W is only valid for n ≫ 1.
```

Here a warning is generated since Fock sampling is not well defined for small `n`. 

A simpler way to sample the vacuum is 

```julia-repl
julia> s = Coherent(0) 
Coherent(0.0 + 0.0im)  # type conversion to ComplexF64.

julia> wigner(s,100)
(ComplexF64[0.33820868828162637 + 0.4407579103538181im, 0.057183146091823775 - 0.2772571883006981im, ...
```

generating two vectors of sampled points `α,α⁺` in the complex plane. In this case, `α = conj(α⁺)`, as we are not working with a doubled phase space.
