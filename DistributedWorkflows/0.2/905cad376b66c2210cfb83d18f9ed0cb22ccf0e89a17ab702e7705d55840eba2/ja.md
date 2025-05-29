```
connect(pnet::Workflow_PetriNet, place::Place, port::Port)
connect(pnet::Workflow_PetriNet, port::Port, place::Place)
```

与えられたペトリネットに対して、指定されたプレースを指定されたポートに接続します。

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


julia> connect(pn, p1, :in)
名前が "hello_julia" のペトリネットで、ポートが1、プレースが3、遷移が1です。


julia> connect(pn, p2, :in)
名前が "hello_julia" のペトリネットで、ポートが2、プレースが3、遷移が1です。


julia> connect(pn, p3, :out)
名前が "hello_julia" のペトリネットで、ポートが3、プレースが3、遷移が1です。

```

さらに [`place`](@ref), [`transition`](@ref), [`arc`](@ref), [`port`](@ref), [`Workflow_PetriNet`](@ref), [`remove`](@ref) を参照してください。
