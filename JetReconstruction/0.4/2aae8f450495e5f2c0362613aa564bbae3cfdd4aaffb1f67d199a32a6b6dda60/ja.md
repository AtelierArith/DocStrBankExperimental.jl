```
tiled_jet_reconstruct(particles::AbstractVector{T}; p::Union{Real, Nothing} = -1,
                           algorithm::Union{JetAlgorithm.Algorithm, Nothing} = nothing,
                           R = 1.0, recombine = +) where {T}
```

ジェットの再構築のためのメインアルゴリズムエントリーポイントで、一般的なジェットタイプTのタイル戦略を使用してジェットを再構築します。

**注意** - 非標準の再結合が使用される場合、JetReconstruction.PseudoJetのために定義されている必要があります。この構造体は内部で使用されます。

このコードは、(rapidity, φ)空間で動作する`k_t`アルゴリズムタイプを使用します。

`algorithm`と`p`（パワー）値の両方を指定する必要はありません。両方が与えられた場合、一貫性がなければ例外がスローされます。

## 引数

  * `particles::AbstractVector{T}`: ジェット再構築の入力として使用される粒子のベクトル。Tはpx、py、pzおよびエネルギー（JetReconstruction名前空間で定義）をサポートしている必要があります。
  * `p::Union{Real, Nothing} = -1`: ジェット再構築アルゴリズムのためのパワーパラメータで、異なるアルゴリズム間の切り替えを行います。
  * `algorithm::Union{JetAlgorithm.Algorithm, Nothing} = nothing`: 使用する明示的なジェットアルゴリズム。
  * `R::Float64 = 1.0`: ジェット再構築アルゴリズムのためのジェット半径パラメータ。
  * `recombine::Function = +`: 擬似ジェットを結合するために使用される再結合関数。

## 戻り値

  * `Vector{PseudoJet}`: 再構築されたジェットのベクトル。

## 例

```julia
tiled_jet_reconstruct(particles::Vector{LorentzVectorHEP}; p = -1, R = 0.4, recombine = +)
```
