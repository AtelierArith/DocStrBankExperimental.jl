```
abstract type AbstractAtom <: SyntaxLeaf end
```

原子は、時には原子的命題、命題文字（または単に*文字*）と呼ばれ、論理的解釈に基づいて真偽を評価できる事実を表します。

原子は無項トークンです（すなわち、構文木の葉にあります）；その原子は`Atom`ではないことに注意してください。

# インターフェース

  * `syntaxstring(s::AbstractAtom; kwargs...)::String`
  * `dual(s::AbstractAtom)::AbstractAtom`
  * `hasdual(s::AbstractAtom)::Bool`

参照： [`AbstractInterpretation`](@ref), [`atoms`](@ref), [`check`](@ref), [`SyntaxToken`](@ref).
