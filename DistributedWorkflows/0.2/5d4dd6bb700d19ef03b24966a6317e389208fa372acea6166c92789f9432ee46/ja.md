```
generate_workflow(pnet::Workflow_PetriNet)
generate_workflow(pnet::Workflow_PetriNet, path::String)
```

ペトリネットの説明に基づいて、XMLワークフローを作成し、指定されたパスのファイルに書き込みます。

# 例

```julia-repl
julia> pn = Workflow_PetriNet("hello_julia")
名前が "hello_julia" のペトリネットで、ポートが0、プレースが0、トランジションが0です。


julia> p1 = place("input1", :string)
制御トークンが作成されたプレース input1。


julia> p2 = place("input2",:string)
制御トークンが作成されたプレース input2。


julia> p3 = place("output",:string)
制御トークンが作成されたプレース output。


julia> t = transition("trans")
トランジション trans が作成されました。


julia> connect(pn, p1,t, :in)
名前が "hello_julia" のペトリネットで、ポートが0、プレースが1、トランジションが1です。


julia> connect(pn, p2,t, :read)
名前が "hello_julia" のペトリネットで、ポートが0、プレースが2、トランジションが1です。


julia> connect(pn, p3,t, :out_many)
名前が "hello_julia" のペトリネットで、ポートが0、プレースが3、トランジションが1です。


julia> connect(pn, p1, :in)
名前が "hello_julia" のペトリネットで、ポートが1、プレースが3、トランジションが1です。


julia> connect(pn, :in, p2)
名前が "hello_julia" のペトリネットで、ポートが2、プレースが3、トランジションが1です。


julia> connect(pn, :out, p3)
名前が "hello_julia" のペトリネットで、ポートが3、プレースが3、トランジションが1です。

# パスが提供されていない場合、生成されたワークフローはホームディレクトリのフォルダ: tmp に保存されます
julia> generate_workflow(pn, "/home/pnet/")
XMLワークフロー parallel_reduce.xpnet が次の場所に書き込まれました: /home/pnet/.

```

他の情報については [`place`](@ref), [`transition`](@ref), [`arc`](@ref), [`port`](@ref), [`Workflow_PetriNet`](@ref), [`connect`](@ref), [`remove`](@ref), [`compile_workflow`](@ref) を参照してください。
