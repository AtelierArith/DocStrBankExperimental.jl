```
⊗(spaces::HilbertSpace...)
```

Create a [`ProductSpace`](@ref) consisting of multiple subspaces. Unicode `\otimes<tab>` alias of [`tensor`](@ref)

# Examples

```
julia> hf = FockSpace(:f)
ℋ(f)

julia> ha = NLevelSpace(:a,2)
ℋ(a)

julia> h = hf⊗ha
ℋ(f) ⊗ ℋ(a)
```
