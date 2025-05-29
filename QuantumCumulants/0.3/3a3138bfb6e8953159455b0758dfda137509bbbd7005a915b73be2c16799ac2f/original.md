```
Transition <: QSym
Transition(h::NLevelSpace,name::Symbol,i,j)
```

Fundamental operator defining a transition from level `j` to level `i` on a [`NLevelSpace`](@ref). The notation corresponds to Dirac notation, i.e. the above is equivalent to `|i⟩⟨j|`.

# Examples

```
julia> ha = NLevelSpace(:a,(:g,:e))
ℋ(a)

julia> σ = Transition(ha,:σ,:g,:e)
σge
```
