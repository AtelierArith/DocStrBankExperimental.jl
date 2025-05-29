```
pushinstances!(md, instance)
```

マルチモーダルデータセットにインスタンスを追加し、データセット自体を返します。

インスタンスは `DataFrameRow` または `AbstractVector` であることができますが、いずれの場合も変数の数と型はデータセットのものと一致する必要があります。
