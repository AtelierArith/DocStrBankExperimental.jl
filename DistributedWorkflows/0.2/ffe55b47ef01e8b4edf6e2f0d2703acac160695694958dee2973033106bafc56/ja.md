```
savefig(pnet::Workflow_PetriNet)
savefig(pnet::Workflow_PetriNet, format::Symbol)
savefig(pnet::Workflow_PetriNet, path::String)
savefig(pnet::Workflow_PetriNet, format::Symbol, path::String)
```

デフォルトでは、このメソッドはペトリネットをXMLワークフローにコンパイルし、ワークフローをコンパイルした後にPNGファイルを生成します。パスが指定されていない場合、ワークフロー画像はホームディレクトリの「tmp/pnet」フォルダに保存されます。

注意: GraphVizによってすべてのファイル形式をサポートしています。例えば、:png, :svg, :jpg, :pdf, :webp

他の形式については、GraphVizのドキュメントを確認してください: https://graphviz.org/docs/outputs/

# 例

```julia-repl
julia> # まずペトリネットの形でワークフローを生成します
julia> pn = Workflow_PetriNet("hello_julia")
名前が「hello_julia」のペトリネットで、ポートが0、プレースが0、トランジションが0です。


julia> p1 = place("input_file1")
プレース「input_file1」が作成されました。


julia> p2 = place("input_file2")
プレース「input_file2」が作成されました。


julia> p3 = place("output_file1")
プレース「output_file1」が作成されました。


julia> p4 = place("output_file2")
プレース「output_file2」が作成されました。


julia> t = transition("hello_jl")
トランジション「hello_jl」が作成されました。


julia> connect(pn,[(p1, :in),(p2, :in),(p3, :out), (p4, :out)], t)
名前が「hello_julia」のペトリネットで、ポートが0、プレースが4、トランジションが1です。


julia> connect(pn, p1, :in)
名前が「hello_julia」のペトリネットで、ポートが1、プレースが4、トランジションが1です。


julia> connect(pn, p2, :in)
名前が「hello_julia」のペトリネットで、ポートが2、プレースが4、トランジションが1です。


julia> connect(pn, p3, :out)
名前が「hello_julia」のペトリネットで、ポートが3、プレースが4、トランジションが1です。


julia> connect(pn, p4, :out)
名前が「hello_julia」のペトリネットで、ポートが4、プレースが4、トランジションが1です。


julia> pn
名前が「hello_julia」のペトリネットで、ポートが4、プレースが4、トランジションが1です。

# これでワークフロー画像を生成します
julia> savefig(pn, :jpg, "/home/pnet")
"ワークフローペトリネットの画像は/home/pnet/hello_julia.jpgにあります"

# 次のコマンドはペトリネットと保存先のパスを取り、指定されたパスに保存されるPNGファイルを生成します。
julia> savefig(pn, "/home/pnet")
"ワークフローペトリネットの画像は/home/pnet/hello_julia.pngにあります"

```

[`Workflow_PetriNet`](@ref)、[`place`](@ref)、[`transition`](@ref)、[`arc`](@ref)、[`port`](@ref)、[`Workflow_PetriNet`](@ref)、[`connect`](@ref)、[`remove`](@ref)、[`compile_workflow`](@ref)、[`generate_workflow`](@ref)も参照してください。
