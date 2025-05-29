```
Workflow_PetriNet(workflow_name::String)
```

空のペトリネットを作成する構造体で、名前は「workflow_name」です。ワークフロー名が提供されていない場合はエラーをスローします。

`connect()`関数を使用してペトリネットを構成し、`remove()`関数を使用してペトリネットのコンポーネントを削除します。

# 例

```julia-repl
julia> pn = Workflow_PetriNet("hello_julia")
名前が「hello_julia」のペトリネットで、ポートが0、場所が0、遷移が0です。


julia> p1 = place("input1", :string)
場所「input1」が作成されました。


julia> p2 = place("input2",:string)
場所「input2」が作成されました。


julia> p3 = place("output",:string)
場所「output」が作成されました。


julia> t = transition("trans")
遷移「trans」が作成されました。


julia> connect(pn, p1, t, :in)
名前が「hello_julia」のペトリネットで、ポートが0、場所が1、遷移が1です。


julia> connect(pn, p2, t, :read)
名前が「hello_julia」のペトリネットで、ポートが0、場所が2、遷移が1です。


julia> connect(pn, p3, t, :out_many)
名前が「hello_julia」のペトリネットで、ポートが0、場所が3、遷移が1です。


julia> connect(pn, p1, :in)
名前が「hello_julia」のペトリネットで、ポートが1、場所が3、遷移が1です。


julia> connect(pn, :in, p2)
名前が「hello_julia」のペトリネットで、ポートが2、場所が3、遷移が1です。


julia> connect(pn, :out, p3)
名前が「hello_julia」のペトリネットで、ポートが3、場所が3、遷移が1です。

```

[`place`](@ref)、[`transition`](@ref)、[`arc`](@ref)、[`port`](@ref)、[`connect`](@ref)、[`remove`](@ref)、[`generate_workflow`](@ref)、[`compile_workflow`](@ref)も参照してください。
