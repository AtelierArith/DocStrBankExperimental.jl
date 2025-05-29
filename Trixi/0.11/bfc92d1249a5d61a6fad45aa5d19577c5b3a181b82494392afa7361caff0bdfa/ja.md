```
T8codeMesh(cmesh::Ptr{t8_cmesh},
           mapping=nothing, polydeg=1, RealT=Float64,
           initial_refinement_level=0)
```

`T8codeMesh`のメインメッシュコンストラクタで、`t8_cmesh`データ構造から非構造的で適合したメッシュをインポートします。

# 引数

  * `cmesh::Ptr{t8_cmesh}`: cmeshオブジェクトへのポインタ。
  * `mapping`: インポートされたメッシュを物理領域に変換するための`NDIMS`変数の関数。アイデンティティマップの場合は`nothing`を使用します。
  * `polydeg::Integer`: メッシュのジオメトリを格納するために使用される多項式の次数。マッピングは、各ツリーに対して指定された次数の補間多項式によって近似されます。デフォルトの`1`は、曲がっていないジオメトリを作成します。インポートされた曲がっていないメッシュを曲げる場合は、より高い値を使用してください。
  * `RealT::Type`: 座標に使用されるべき型。
  * `initial_refinement_level::Integer`: シミュレーション開始前にメッシュを均一にこのレベルまで細分化します。
