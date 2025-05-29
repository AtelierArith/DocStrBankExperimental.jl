```
getsamples(M::Union{MPS,MPO,ITensor}, bases::Matrix::Matrix{<:String}, nshots::int; kwargs...)
getsamples(M::Union{MPS,MPO,ITensor}, bases::Vector{<:Vector}, nshots::Int; kwargs...) =
```

入力 `bases` に従って測定のセットを生成し、各基準ごとに `nshots` 測定を行います。単一の測定では、深さ1のユニタリ $U$ が入力状態 $M$ に `basis` に従って適用されます。結果 $\sigma = (\sigma_1,\sigma_2,\dots)$ を記録する確率は、$U$ によって定義された基準において次のようになります。

  * $$
    P(\sigma) = |\langle\sigma|U\psi\rangle|^2
    $$

    ,   もし $M = |\psi\rangle$ が `MPS` の場合。
  * $$
    P(\sigma) = \langle\sigma|U\rho U^\dagger|\sigma\rangle
    $$

    ,   もし $M = \rho$ が `MPO` の場合。
