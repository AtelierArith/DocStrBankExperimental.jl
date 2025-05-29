```
deepsetindex!(A::AbstractArray, x, idxs...)
deepsetindex!(A::AbstractArray{<:AbstractArray,N}, x, idxs...) where {N}
```

フラットまたはネストされた配列に対する再帰的な `setindex!`。A が配列の配列である場合、`idxs` の最初の `N` エントリを `A` に使用し、残りを内部配列に使用します。A がネストされた配列でない場合、`deepsetindex!` は `setindex!` と同等です。

[`deepgetindex`](@ref) と [`deepview`](@ref) も参照してください。
