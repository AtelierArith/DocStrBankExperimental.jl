```
T8codeMesh(conn::Ptr{p4est_connectivity}; kwargs...)
```

`p4est_connectivity`データ構造から非構造的で適合したメッシュをインポートする`T8codeMesh`のメインメッシュコンストラクタ。

# 引数

  * `conn::Ptr{p4est_connectivity}`: P4est接続オブジェクトへのポインタ。
  * `mapping`: インポートされたメッシュを物理領域に変換するための`NDIMS`変数の関数。恒等写像には`nothing`を使用します。
  * `polydeg::Integer`: メッシュのジオメトリを格納するために使用される多項式の次数。マッピングは、各ツリーに対して指定された次数の補間多項式によって近似されます。デフォルトの`1`は曲がっていないジオメトリを作成します。インポートされた曲がっていないメッシュを曲げる場合は、より高い値を使用してください。
  * `RealT::Type`: 座標に使用されるべき型。
  * `initial_refinement_level::Integer`: シミュレーション開始前にメッシュを均一にこのレベルまで細分化します。
