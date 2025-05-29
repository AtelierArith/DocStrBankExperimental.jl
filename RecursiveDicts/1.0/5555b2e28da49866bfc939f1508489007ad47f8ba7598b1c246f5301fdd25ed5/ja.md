```
RecursiveDict{K,V} <: AbstractDict{K,Union{V,RecursiveDict}}
```

自身のインスタンスが常に有効な値である `Dict`。したがって、`RecursiveDict{String,String}` は `String` キーを持ち、値は `String` または `RecursiveDict{String,String}` のいずれかである可能性があります。これを `RecursiveDict{String,Union{String,RecursiveDict{String,String}}}` と書くのは無害ですが、必ずしも必要ではなく、シグネチャが示すように、最終的には基本ケースを提供する必要があります。

`Dict` を受け取るすべての `Base` メソッドを実装しています。`convert` は、データ構造を提供するラップされた `Dict` を返します。これは共有参照として意味し、提供された `Dict` に対する変更は `RecursiveDict` にも反映されるため、このデータ構造は `Dict` を期待する場所で使用できますが、少し注意が必要です。

`Dict{K,V}` も `RecursiveDict{K,V}` に変換でき、コピーは行われません。
