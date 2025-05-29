```
svd(T::BlockSparseTensor{<:Number,2}; kwargs...)
```

順序2のBlockSparseTensorのsvd。

この関数は、行/列ごとに1つのブロックがあることを前提としています。そうでない場合は失敗します。この前提により、結果は別々のブロックの密なsvdから計算できるようになります。
