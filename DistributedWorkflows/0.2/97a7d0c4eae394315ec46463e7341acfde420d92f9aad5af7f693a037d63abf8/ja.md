```
port(type::Symbol, place::Place)
```

指定された場所に対してアークタイプに関するポートを作成します。注意: 許可されているポートタイプは次のいずれかです: :in, :out, :inout

# 例

```julia-repl
julia> p1 = place("input1", :string)
Place "input1" created.


julia> port(:in, p1)
A port of type "in" connected to place "input1".

```

関連項目としては [`place`](@ref), [`Workflow_PetriNet`](@ref), [`connect`](@ref), [`remove`](@ref) があります。
