```
plain_jet_reconstruct(particles::AbstractVector{T}; p::Union{Real, Nothing} = -1,
                           algorithm::Union{JetAlgorithm.Algorithm, Nothing} = nothing,
                           R = 1.0, recombine = +) where {T}
```

プレーンアルゴリズムを使用してppジェット再構築を行います。

# 引数

  * `particles::AbstractVector{T}`: ジェット再構築に使用される粒子のベクトル。適切な4ベクトルメソッド（pt2()、phi()、rapidity()、px()、py()、pz()、energy()）をサポートする任意の粒子の配列が使用できます。
  * `p::Union{Real, Nothing} = -1`: ジェット再構築に使用されるべきべき乗値。
  * `algorithm::Union{JetAlgorithm, Nothing} = nothing`: 使用する明示的なジェットアルゴリズム。
  * `R::Float64 = 1.0`: ジェット再構築に使用される半径パラメータ。
  * `recombine::Function = +`: ジェット再構築に使用される再結合関数。

**注意** `particles`引数について、4ベクトルメソッドはJetReconstructionパッケージの名前空間に存在する必要があります。

このコードは、(rapidity, φ)空間で動作する`k_t`アルゴリズムタイプを使用します。

`algorithm`と`p`（べき乗）値の両方を指定する必要はありません。両方が指定されている場合は、一貫性がなければ例外がスローされます。

# 戻り値

  * `Vector{PseudoJet}`: 再構築されたジェットのベクトル。

# 例

```julia
jets = plain_jet_reconstruct(particles; p = -1, R = 0.4)
jets = plain_jet_reconstruct(particles; algorithm = JetAlgorithm.Kt, R = 1.0)
```
