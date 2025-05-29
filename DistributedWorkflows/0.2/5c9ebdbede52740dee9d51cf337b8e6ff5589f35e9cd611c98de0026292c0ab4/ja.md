```
remove(pnet::Workflow_PetriNet, arc::Arc)
```

指定されたペトリネットからアークを削除します。  

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


julia> a1 = arc(p1,t,:in)
プレース: input1 からトランジション: initial_transition への "in" タイプのアークです。


julia> pn.arcs
3-element Vector{DistributedWorkflows.Arc}:
 プレース: input1 からトランジション: initial_transition への "in" タイプのアークです。

 プレース: input2 からトランジション: initial_transition への "read" タイプのアークです。

 プレース: output_result からトランジション: initial_transition への "out_many" タイプのアークです。


julia> remove(pn, a1)
名前 "hello_julia" のペトリネットで、ポートが3、プレースが3、トランジションが1です。


julia> pn.arcs
2-element Vector{DistributedWorkflows.Arc}:
 プレース: input2 からトランジション: initial_transition への "read" タイプのアークです。

 プレース: output_result からトランジション: initial_transition への "out_many" タイプのアークです。


```

他の情報は [`place`](@ref), [`transition`](@ref), [`arc`](@ref), [`port`](@ref), [`Workflow_PetriNet`](@ref), [`connect`](@ref) を参照してください。
