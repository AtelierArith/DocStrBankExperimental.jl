```
connect(pnet::Workflow_PetriNet, place::Place, transition::Transition, arc_type::Symbol)
connect(pnet::Workflow_PetriNet, transition::Transition, place::Place, arc_type::Symbol)
```

与えられたペトリネットは、指定されたアークタイプでプレースをトランジションに接続します。

# 例

```julia-repl
# 空のペトリネットを初期化します。
julia> pn = Workflow_PetriNet("hello_julia")
名前 "hello_julia" のペトリネットで、ポートが0、プレースが0、トランジションが0です。


julia> p1 = place("input1", :string)
プレース "input1" が作成されました。


julia> p2 = place("input2",:string)
プレース "input2" が作成されました。


julia> p3 = place("output",:string)
プレース "output" が作成されました。


julia> t = transition("transition1")
トランジション "transition1" が作成されました。


julia> connect(pn, p1,t, :in)
名前 "hello_julia" のペトリネットで、ポートが0、プレースが1、トランジションが1です。


julia> connect(pn, p2,t, :read)
名前 "hello_julia" のペトリネットで、ポートが0、プレースが2、トランジションが1です。


julia> connect(pn, p3,t, :out_many)
名前 "hello_julia" のペトリネットで、ポートが0、プレースが3、トランジションが1です。


julia> connect(pn, p1, :in)
名前 "hello_julia" のペトリネットで、ポートが1、プレースが3、トランジションが1です。


julia> connect(pn, :in, p2)
名前 "hello_julia" のペトリネットで、ポートが2、プレースが3、トランジションが1です。


julia> connect(pn, :out, p3)
名前 "hello_julia" のペトリネットで、ポートが3、プレースが3、トランジションが1です。

```

さらに [`place`](@ref), [`transition`](@ref), [`arc`](@ref), [`port`](@ref), [`Workflow_PetriNet`](@ref), [`remove`](@ref) を参照してください。
