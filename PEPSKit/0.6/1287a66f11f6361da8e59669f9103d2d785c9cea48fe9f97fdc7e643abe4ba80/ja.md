```julia
struct HalfInfiniteProjector{S<:PEPSKit.SVDAdjoint, T} <: PEPSKit.ProjectorAlgorithm
```

半無限CTMRG環境のSVDからプロジェクタを実装するプロジェクタアルゴリズム。

## フィールド

  * `svd_alg::PEPSKit.SVDAdjoint`
  * `trscheme::Any`
  * `verbosity::Int64`

## コンストラクタ

```
HalfInfiniteProjector(; kwargs...)
```

以下のキーワード引数に基づいて半無限プロジェクタアルゴリズムを構築します：

  * `svd_alg::Union{<:SVDAdjoint,NamedTuple}=SVDAdjoint()` : 逆ルールを含むSVDアルゴリズム。 [`SVDAdjoint`](@ref)を参照してください。
  * `trscheme::Union{TruncationScheme,NamedTuple}=(; alg::Symbol=:fixedspace)` : プロジェクタ計算のための切り捨てスキームで、結果の仮想空間を制御します。ここで、`alg`は以下のいずれかになります：

      * `:fixedspace` : 投影中に仮想空間を固定
      * `:notrunc` : 特異値は切り捨てられず、実行されるSVDは正確
      * `:truncerr` : 追加で誤差閾値`η`を供給；`η`の最大仮想次元に切り捨て
      * `:truncdim` : 追加で切り捨て次元`η`を供給；切り捨てられた値の2ノルムが`η`より小さくなるように切り捨て
      * `:truncspace` : 追加で切り捨て空間`η`を供給；供給されたベクトル空間に従って切り捨て
      * `:truncbelow` : 追加で特異値カットオフ`η`を供給；保持される特異値がすべて`η`より大きくなるように切り捨て
  * `verbosity::Int=0` : プロジェクタ出力の冗長性で、以下のようになります：

    0. 出力情報を抑制
    1. 特異値の重複警告を印刷
