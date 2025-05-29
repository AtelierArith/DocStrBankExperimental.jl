```
dot(y::PDVec, A::AbstractObservable, x::PDVec[, w::PDWorkingMemory])
```

`y ⋅ A ⋅ x` を実行します。作業メモリ `w` は、非対角行列 `A` を使用したスレッド/分散操作を容易にするために必要です。必要に応じて、新しいインスタンスが割り当てられます。`A` は演算子のタプルに置き換えることができます。

[`PDVec`](@ref)、[`PDWorkingMemory`](@ref) を参照してください。
