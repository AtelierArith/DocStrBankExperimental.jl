```
connect(pnet::Workflow_PetriNet, port_type::Symbol, place::Place)
connect(pnet::Workflow_PetriNet, place::Place, port_type::Symbol)
```

与えられたペトリネットに対して、指定されたプレースをポート名port*nameおよびポートタイプport*typeに接続します。

# 例

```julia-repl
julia> pn = Workflow_PetriNet("hello_julia")
名前が "hello_julia" のペトリネットで、ポートが0、プレースが0、遷移が0です。


julia> p1 = place("input1", :string)
プレース "input1" が作成されました。


julia> p2 = place("input2", :string)
プレース "input2" が作成されました。


julia> p3 = place("output_result", :string)
プレース "output_result" が作成されました。


julia> t = transition("initial_transition")
遷移 "initial_transition" が作成されました。


julia> connect(pn,[(p1, :in),(p2, :read),(p3, :out_many)], t)
名前が "hello_julia" のペトリネットで、ポートが0、プレースが3、遷移が1です。

julia> prt = port(:in, p1)
プレース "input1" に接続されたタイプ "in" のポートです。


julia> connect(pn, p1, prt)
名前が "hello_julia" のペトリネットで、ポートが1、プレースが3、遷移が1です。


```

[`place`](@ref)、[`transition`](@ref)、[`arc`](@ref)、[`port`](@ref)、[`Workflow_PetriNet`](@ref)、[`remove`](@ref) も参照してください。
