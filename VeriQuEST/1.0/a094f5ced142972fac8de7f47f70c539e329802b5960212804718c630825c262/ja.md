```
MBQCGraph(graph,input,output)
```

  * MBQCで使用されるグラフを表す構造体。コンテナはグラフと入力および出力のセットを保持します。

# パラメータ

  * `graph`: MBQCに適した任意のグラフ
  * `input`: MBQCInput型
  * `output`: MBQCOutput型

# 例

```
julia> using Graphs # using Pkg; Pkg.add("Graphs") はインストールされていません
julia> graph = Graphs.grid([1,4]) # 4つの頂点を持つ1次元クラスタグラフ（パスグラフ）
julia> indices,values = (1),(0)
julia> input  = MBQCInput(indices,values)
julia> indices = (4)
julia> output  = MBQCOutput(indices)
julia> mbqc_graph = MBQCGraph(graph,input,output)
```
