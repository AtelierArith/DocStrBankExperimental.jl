```
contraction(Φₗₖ::AbstractArray{T,3},Aₖ::AbstractArray{T,3}) -> AbstractArray{T,4}
contraction(Φₗₖ::AbstractArray{T,3},Aₖ::AbstractArray{T,3},Φᵣₖ::AbstractArray{T,3}) -> AbstractArray{T,6}
```

テンソルトレインコアの収束、（ペトロフ-）ガレルキン射影の結果。`Aₖ`の`Φₗₖ`による収束は、TTコア`Aₖ`の（左、テスト）TTコア`Φₗₖ`による左収束であり、`Aₖ`の`Φᵣₖ`による収束は、TTコア`Aₖ`の（右、試行）TTコア`Φᵣₖ`による右収束です。`N`個の因子を含む収束の出力の次元は次のようになります：`3N - N = 2N`。
