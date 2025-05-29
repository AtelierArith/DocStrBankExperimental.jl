```
create_ubqc_resource(para)
```

提供されたパラメータを使用してUBQC（Universal Blind Quantum Computation）リソースを作成します。この関数は、テストと計算の色を初期化し、逆流を計算し、パラメータを含む辞書を作成します。その後、作成した辞書を引数として`create_graph_resource`関数を呼び出します。

# 引数

  * `para`: UBQCリソースのためのパラメータを含む辞書。以下のキーを含む必要があります: `:input`, `:output`, `:graph`, `:secret_angles`, および `:forward_flow`。

# 戻り値

  * `create_graph_resource`関数の結果。

# 例

```julia
para = (args)::NamedTuple # 関数特有の引数
ubqc_resource = create_ubqc_resource(para)
```
