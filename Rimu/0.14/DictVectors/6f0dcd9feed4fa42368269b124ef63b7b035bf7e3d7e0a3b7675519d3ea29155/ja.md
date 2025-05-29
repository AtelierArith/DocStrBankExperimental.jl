```
mul!(y::PDVec, A::AbstractObservable, x::PDVec[, w::PDWorkingMemory])
```

`y = A * x`をインプレースで実行します。スレッド/分散操作を促進するために作業メモリ`w`が必要です。渡されない場合は新しいインスタンスが割り当てられます。`y`と`x`は同じベクトルである可能性があります。

[`PDVec`](@ref)、[`PDWorkingMemory`](@ref)、[`AbstractObservable`](@ref)を参照してください。
