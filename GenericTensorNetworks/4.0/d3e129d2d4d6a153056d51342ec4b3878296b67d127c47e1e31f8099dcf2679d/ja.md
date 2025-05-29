```
mis_compactify!(tropicaltensor; potential=nothing)
```

最大独立集合問題のためにトロピカルテンソルをコンパクト化します。これは、これらのエントリをゼロに設定することによっていくつかのエントリを排除します。これは、これらのエントリを削除しても親グラフのMISサイズが変わらないという基準によります（参照は追加されます）。

### 引数

  * `tropicaltensor::AbstractArray{T}`: トロピカルテンソル

### キーワード引数

  * `potential=nothing`: 各オープン頂点からの最大可能MIS寄与
