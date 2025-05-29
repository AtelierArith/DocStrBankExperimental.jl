```
mutable struct Alignment{A,T} where {A, T<:Integer}
```

```
    data::Matrix{T}
    alphabet::Union{Nothing, Alphabet{A,T}}
    weights::Vector{Float64} = ones(size(dat,1))/size(dat,1) # 系列の系統的重み
    names::Vector{String} = fill("", size(dat, 1))
```

生物学的配列は型 `T<:Integer` のベクトルとして表されます。`data` は *列* にシーケンスを格納します： `size(dat)` はタプル `(L, M)` を返し、`L` は長さ、`M` はシーケンスの数です。表示されると、`data` は従来のアライメントに合わせて `MxL` 行列として表示されます。

`alphabet{A,T}` は `data` の整数と生物学的記号の型 `A`（ヌクレオチド、アミノ酸など）とのマッピングを表します。`nothing` の場合、アライメントは生物学的配列にマッピングできません。

`weights` は系統的重みを表し、`1/M` に初期化されます。これらは合計が 1 でなければなりません。`names` はシーケンスのラベルであり、`data` の列と同じ順序であることが期待されます。これらは一意である必要はなく、無視することができます。

**重要**：行列から構築される場合、シーケンスが *列* に格納されていると仮定します。

## メソッド

  * `getindex(X::Alignment, i)` は行列/ベクトル `X.data[:, i]` を返します。
  * `for s in X::Alignment` はシーケンスを反復処理します。
  * `eachsequence(X::Alignment)` はシーケンスに対するイテレータを返します（`Vector{Int}`）。
  * `eachsequence_weighted(X::Alignment)` はシーケンスと重みをタプルとして返すイテレータを返します。
  * `subaln(X::Alignment, idx)` はインデックス `idx` によって定義されたサブアラインメントを構築します。
