```
remove(pnet::Workflow_PetriNet,  transition::Transition)
```

指定されたペトリネットから遷移を削除します。  

# 例

```julia-repl
julia> pn = Workflow_PetriNet("hello_julia")
名前が "hello_julia" のペトリネットで、ポートが0、場所が0、遷移が0です。


julia> p1 = place("input1", :string)
場所 "input1" が作成されました。


julia> p2 = place("input2", :string)
場所 "input2" が作成されました。


julia> p3 = place("output_result", :string)
場所 "output_result" が作成されました。


julia> t = transition("initial_transition")
遷移 "initial_transition" が作成されました。


julia> connect(pn,[(p1, :in),(p2, :read),(p3, :out_many)], t)
名前が "hello_julia" のペトリネットで、ポートが0、場所が3、遷移が1です。


julia> connect(pn, p1, :in)
名前が "hello_julia" のペトリネットで、ポートが1、場所が3、遷移が1です。


julia> connect(pn, p2, :in)
名前が "hello_julia" のペトリネットで、ポートが2、場所が3、遷移が1です。


julia> connect(pn, p3, :out)
名前が "hello_julia" のペトリネットで、ポートが3、場所が3、遷移が1です。


julia> pn.transitions
1-element Vector{DistributedWorkflows.Transition}:
 遷移 "initial_transition" が作成されました。


julia> remove(pn, t)
名前が "hello_julia" のペトリネットで、ポートが2、場所が2、遷移が0です。


julia> pn.transitions
DistributedWorkflows.Transition[]


```

他の情報は [`place`](@ref), [`transition`](@ref), [`arc`](@ref), [`port`](@ref), [`Workflow_PetriNet`](@ref), [`connect`](@ref) を参照してください。
