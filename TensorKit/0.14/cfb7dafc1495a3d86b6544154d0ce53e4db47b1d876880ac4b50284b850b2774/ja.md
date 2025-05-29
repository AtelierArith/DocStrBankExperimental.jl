```
repartition!(tdst::AbstractTensorMap{S}, tsrc::AbstractTensorMap{S}) where {S} -> tdst
```

`tsrc`のインデックスの再分配の結果を`tdst`に書き込みます。これは、入出力インデックスの数だけを変更する転置の特別なケースです。

新しいテンソルを作成するには、[`repartition`](@ref)を参照してください。
