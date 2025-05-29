```
transition(name::String)
transition(name::String, condition::String)
```

PetriネットオブジェクトのためのTransition型のオブジェクトを作成します。条件文字列が与えられた場合、その遷移は条件付き遷移になります。

注意: 条件および/または式はFortranスタイルの式に従います。次のような式が文字列にラップされる可能性があります: 比較式: :lt: :le: :gt: :ge: :ne: :eq: ブール式: :or: :and: :not: 演算: +, -, *, /, :=

使用方法の例を参照してください。

# 例

```julia-repl
julia> transition("transition1")
Transition "transition1" created.

julia> transition("do_stuff", "counter :eq: 0UL")
A conditional transition "do_stuff" created.

```

[`place`](@ref), [`arc`](@ref), [`Workflow_PetriNet`](@ref), [`connect`](@ref), [`remove`](@ref)も参照してください。
