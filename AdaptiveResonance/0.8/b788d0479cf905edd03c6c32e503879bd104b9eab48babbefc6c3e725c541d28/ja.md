```julia
classify(
    art::AdaptiveResonance.ARTModule,
    x::AbstractMatrix{T} where T<:Real;
    preprocessed,
    get_bmu
) -> Any

```

# 概要

ARTモデルを使用して'x'のカテゴリを予測します。

予測されたカテゴリ'y_hat'を返します。

# 引数

  * `art::ARTModule`: バッチ推論に使用するARTまたはARTMAPモジュール。
  * `x::RealMatrix`: 特徴の行を持つサンプルの列を含む2-Dデータセット。
  * `preprocessed::Bool=false`: データがすでに補完符号化されているかどうかのフラグ。
  * `get_bmu::Bool=false`: モデルが完全な不一致の場合に最適一致ユニットラベルを返すべきかどうかのフラグ。

# 例

```julia-repl
julia> my_DDVFA = DDVFA()
DDVFA
    opts: opts_DDVFA
    ...
julia> x, y = load_data()
julia> train!(my_DDVFA, x)
julia> y_hat = classify(my_DDVFA, y)
```

# メソッドリスト / 定義場所

```julia
classify(art, x; preprocessed, get_bmu)
```

[`packages/AdaptiveResonance/wgSPV/src/lib/common.jl:554`](file:///home/terasaki/.julia/packages/AdaptiveResonance/wgSPV/src/lib/common.jl)で定義されています。
