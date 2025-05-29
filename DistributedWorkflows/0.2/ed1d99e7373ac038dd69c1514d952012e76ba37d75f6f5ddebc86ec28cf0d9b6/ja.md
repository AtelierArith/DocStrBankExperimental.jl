```
transition(name::String, exp::Vector{String})
transition(name::String, exp::Vector{String}, condition::String)
```

式を含むペトリネットオブジェクトのタイプTransitionのオブジェクトを作成します。条件文字列が指定されている場合、その遷移は条件付き遷移です。

注意: 条件および/または式はFortranスタイルの式に従います。次のような式を文字列でラップすることができます: 比較式:  :lt: :le: :gt: :ge: :ne: :eq: 論理式:  :or: :and: :not: 演算:  +, -, *, /, :=

使用方法の例を参照してください。

# 例

```julia-repl
julia> transition("transition1")
Transition "transition1" created.

julia> transition("do_stuff", "counter :eq: 0UL")
A conditional transition "do_stuff" created.

```

[`place`](@ref)、[`arc`](@ref)、[`Workflow_PetriNet`](@ref)、[`connect`](@ref)、[`remove`](@ref)も参照してください。
