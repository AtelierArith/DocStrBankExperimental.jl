```
resample!(v::AbstractArray{T, 1}, x::AbstractUncertainValue)
resample!(v::MVector{N, T}, x::AbstractUncertainValue) where {N, T}
resample!(v::FieldVector{N, T}, x::AbstractUncertainValue) where {N, T}

resample!(v::MVector{N, T}, x::Vararg{AbstractUncertainValue, N}) where {N, T}
resample!(v::FieldVector{N, T}, x::Vararg{AbstractUncertainValue, N}) where {N, T}

resample!(v::AbstractArray{T, 1}, x::UVAL_COLLECTION_TYPES) where T
resample!(v::AbstractArray{T, 2}, x::UVAL_COLLECTION_TYPES) where T

resample!(idxs::AbstractArray{T, 1}, vals::AbstractArray{T, 1}, 
    x::AbstractUncertainIndexValueDataset) where T
resample!(idxs::AbstractArray{T, 2}, vals::AbstractArray{T, 2}, 
    x::AbstractUncertainIndexValueDataset) where T
```

不確実な値 `x`、または不確実な値のコレクション `x` を、事前に割り当てられたコンテナ `v` に再サンプリングします。

## 不確実な値

  * `x` が単一の不確実な値であり、`v` がベクトルのようなものであれば、`v` に `x` の `N` 回のサンプリングを埋め込みます。長さ `N` のベクトル、`MVector{N, T}` または `FieldVector{N, T}` で動作します。

## 不確実なコレクション

不確実なコレクションは、長さ `N` の `Vector{AbstractUncertainValue}`、`AbstractUncertainValueDataset`、または `NTuple{N, AbstractUncertainValue}` である可能性があります。 [`UVAL_COLLECTION_TYPES`](@ref) も参照してください。

  * `x` が不確実な値のコレクションであり、`v` がベクトルのようなものであれば、`v[i]` に `x[i]` のサンプリングを埋め込みます（`i = 1:N` の場合）。
  * `x` が不確実な値のコレクションであり、`v` が2D配列であれば、`v` の `i` 番目の列に `x` の `i` 番目の不確実な値の `length(x)` 回のサンプリングを埋め込みます。

## 不確実なインデックス-値コレクション

  * 2つの可変ベクトルのようなコンテナ `idxs` と `vals` が、不確実なインデックス-値データセット `x` と共に提供される場合、`idxs[i]` に `x.indices[i]` からのランダムなサンプリングを埋め込み、`vals[i]` に `x.values[i]` からのランダムなサンプリングを埋め込みます。
  * 2つの可変行列のようなコンテナ `idxs` と `vals` が、不確実なインデックス-値データセット `x` と共に提供される場合（`idxs` と `vals` の両方の列数が `length(x)` と一致する場合）、`idxs` の `i` 番目の列に `x.indices[i]` からの `size(idxs, 1)` 回のサンプリングを埋め込み、`vals` の `i` 番目の列に `x.values[i]` からの `size(idxs, 1)` 回のサンプリングを埋め込みます。
