```
inlinedisplay(i::AbstractAssignment)
```

割り当ての文字列表現を提供します。

# 例

```julia-repl
julia> SoleLogics.inlinedisplay(TruthDict(["a" => true, "b" => false, "c" => true]))
"TruthDict([c => ⊤, b => ⊥, a => ⊤])"

julia> SoleLogics.inlinedisplay(TruthDict(1:4, false))
"TruthDict([4 => ⊥, 2 => ⊥, 3 => ⊥, 1 => ⊥])"
```

他にも [`AbstractAssignment`](@ref) や [`TruthDict`](@ref) を参照してください。
