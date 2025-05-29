```
deepview(A::AbstractArray, idxs...)
deepview(A::AbstractArray{<:AbstractArray, N}, idxs...) where {N}
```

フラットまたはネストされた配列に対する再帰的な `view`。A が配列の配列である場合、`idxs` の最初の `N` エントリを `A` に使用し、残りを内部配列に使用します。A がネストされた配列でない場合、`deepview` は `view` と同等です。

[`deepgetindex`](@ref) と [`deepsetindex!`](@ref) も参照してください。
