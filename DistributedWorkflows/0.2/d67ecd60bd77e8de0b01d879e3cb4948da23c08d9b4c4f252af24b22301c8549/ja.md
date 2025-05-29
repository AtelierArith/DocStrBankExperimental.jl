```
connect(pnet::Workflow_PetriNet, places_arcs::Vector{Tuple{Place, Symbol}}, transition::Transition)
connect(pnet::Workflow_PetriNet, transition::Transition, places_arcs::Vector{Tuple{Place, Symbol}})
```

与えられたペトリネットに対して、タプルのベクター（場所、アークタイプ）を指定された遷移に接続します。

# 例

```julia-repl
julia> pn = Workflow_PetriNet("hello_julia")
名前 "hello_julia" のペトリネットで、ポートが0、場所が0、遷移が0です。


julia> p1 = place("input1", :string)
場所 "input1" が作成されました。


julia> p2 = place("input2", :string)
場所 "input2" が作成されました。


julia> p3 = place("output_result", :string)
場所 "output_result" が作成されました。


julia> t = transition("initial_transition")
遷移 "initial_transition" が作成されました。


julia> connect(pn,[(p1, :in),(p2, :read),(p3, :out_many)], t)
名前 "hello_julia" のペトリネットで、ポートが0、場所が3、遷移が1です。


```

他にも [`place`](@ref), [`transition`](@ref), [`arc`](@ref), [`port`](@ref), [`Workflow_PetriNet`](@ref), [`remove`](@ref) を参照してください。
