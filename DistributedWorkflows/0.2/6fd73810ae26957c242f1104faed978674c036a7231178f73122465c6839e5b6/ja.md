```
remove(pnet::Workflow_PetriNet, place::Place)
```

指定されたペトリネットからプレースを削除します。  

# 例

```julia-repl
julia> pn = Workflow_PetriNet("hello_julia")
名前 "hello_julia" のペトリネットで、ポートが0、プレースが0、トランジションが0です。


julia> p1 = place("input1", :string)
プレース "input1" が作成されました。


julia> p2 = place("input2", :string)
プレース "input2" が作成されました。


julia> p3 = place("output_result", :string)
プレース "output_result" が作成されました。


julia> t = transition("initial_transition")
トランジション "initial_transition" が作成されました。


julia> connect(pn,[(p1, :in),(p2, :read),(p3, :out_many)], t)
名前 "hello_julia" のペトリネットで、ポートが0、プレースが3、トランジションが1です。


julia> connect(pn, p1, :in)
名前 "hello_julia" のペトリネットで、ポートが1、プレースが3、トランジションが1です。


julia> connect(pn, p2, :in)
名前 "hello_julia" のペトリネットで、ポートが2、プレースが3、トランジションが1です。


julia> connect(pn, p3, :out)
名前 "hello_julia" のペトリネットで、ポートが3、プレースが3、トランジションが1です。


julia> pn.places
3-element Vector{DistributedWorkflows.Place}:
 プレース "input1" が作成されました。

 プレース "input2" が作成されました。

 プレース "output_result" が作成されました。


julia> remove(pn, p1)
名前 "hello_julia" のペトリネットで、ポートが2、プレースが2、トランジションが1です。


julia> pn.places
2-element Vector{DistributedWorkflows.Place}:
 プレース "input2" が作成されました。

 プレース "output_result" が作成されました。


```

[`place`](@ref)、[`transition`](@ref)、[`arc`](@ref)、[`port`](@ref)、[`Workflow_PetriNet`](@ref)、[`connect`](@ref) も参照してください。
