```
struct Atom{V} <: SyntaxLeaf
    value::V
end
```

原子は、時には原子的命題、命題文字（または単に*文字*）と呼ばれ、型 `Atom{V}` は論理的解釈に基づいて真偽を評価できる事実を表す `value::V` をラップします。

原子は無項トークンです（すなわち、構文木の葉にあります）；その原子は `Atom` であることはできません。

さらに [`AbstractInterpretation`](@ref)、[`atoms`](@ref)、[`check`](@ref)、[`SyntaxToken`](@ref) を参照してください。
