```
sample(::Type{T<:Real}=Int, A::AbstractArray, n_sim::Int; [dims=:], [n_cat=nothing])
```

独立したカテゴリ分布に対応する分布から `n_sim` サンプルを引き出し、確率質量ベクトル `A` によって定義される結果を、入力 `A`、カテゴリの数 `n_cat`、および（潜在的な）次元削減 `dims` によって決定される十分なサイズと次元の `eltype` `T` の配列に格納します。

`dims` は、`A` が配列の配列である場合に `A` のインデックスでインプレースの合計を指定するために使用されるオプションのキーワード引数です。`n_cat` はオプションで指定することもでき、利用可能なデータから推測されることもあります。妥当性インデックスは常にチェックされます。

最も単純なケースでは、`A` は単一の確率質量ベクトルであり、互換性のある型は `AbstractVector{<:Real}`、`SparseVector{<:Real, <:Integer}`、および `AbstractVector{Tuple{<:Integer, <:Real}}` です。最後のものは単にスパースベクトルの別の表現です。

第二のケースでは、`A` は `AbstractArray{V, N} where {V, N}` であり、ここで `V` は単一の確率質量ベクトルに対して上記で指定された型のいずれかです。つまり、ベクトルの配列です。

第三のケースでは、`A` は `AbstractArray{W, M} where {W<:AbstractArray{V, N}, M} where {V, N}` であり、ここで `W` は第二のケースで指定された型のいずれかです。言い換えれば、ベクトルの配列の配列です。

参照: [`tsample`](@ref), [`vsample`](@ref), [`vtsample`](@ref)
