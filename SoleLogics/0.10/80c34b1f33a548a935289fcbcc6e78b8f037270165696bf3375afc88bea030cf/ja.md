```
interpret(a::AbstractAtom, i::AbstractAssignment, args...; kwargs...)::SyntaxLeaf
```

[`AbstractAssignment`](@ref) に含まれる [`Atom`](@ref) に対応する値を返します。単一の原子を解釈する際に、ルックアップが失敗した場合は、原子自体を返します。

# 例

```julia-repl
julia>interpret(Atom("a"), TruthDict(["a" => true, "b" => false, "c" => true]))
⊤

julia>interpret(Atom(3), TruthDict(1:4, false))
⊥
```

他にも [`AbstractAssignment`](@ref)、[`Atom`](@ref)、[`DefaultedTruthDict`](@ref)、[`TruthDict`](@ref) を参照してください。
