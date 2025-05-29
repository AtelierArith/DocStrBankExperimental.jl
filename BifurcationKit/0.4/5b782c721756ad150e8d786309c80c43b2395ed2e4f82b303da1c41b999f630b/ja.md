```julia
struct SpecialPoint{T, Tp, Tv, Tvτ} <: BifurcationKit.AbstractBifurcationPoint
```

曲線上の特別な点を記録するための構造体。この構造体には、記録される特別な点の2つのタイプがあります：分岐点とイベント（詳細は https://bifurcationkit.github.io/BifurcationKitDocs.jl/dev/EventCallback/ を参照）。

## 関連メソッド

  * `BifurcationKit.type(::SpecialPoint)` は分岐タイプを返します（`::Symbol`）
  * `type::Symbol`: 特別な点の説明。イベントの場合、このフィールドはユーザーがイベントに渡した名前、またはデフォルトの `:userD`, `:userC` を記録します。分岐点の場合、次のいずれかになります：

    ```
    - :bp 分岐点、虚数軸を横切る単純固有値
    - :fold 折りたたみ点
    - :hopf ホップ点
    - :nd 文書化されていない分岐点。複数の固有値が交差することによって検出されます。一般的に対称性のある問題や、連続ステップサイズが大きすぎて2つの異なる分岐点が合併する場合に発生します。
    - :cusp カスプ点
    - :gh 一般化ホップ点（バウティン点とも呼ばれる）
    - :bt ボグダノフ-タケンス点
    - :zh ゼロ-ホップ点
    - :hh ホップ-ホップ点
    - :ns ネイマーク-サッカー点
    - :pd 周期倍増点
    - :R1 周期軌道の強い共鳴 1:1
    - :R2 周期軌道の強い共鳴 1:2
    - :R3 周期軌道の強い共鳴 1:3
    - :R4 周期軌道の強い共鳴 1:4
    - :foldFlip 周期軌道の折りたたみ / フリップ
    - :foldNS 周期軌道の折りたたみ / ネイマーク-サッカー
    - :pdNS  周期倍増 / ネイマーク-サッカーの周期軌道
    - :gpd 周期軌道の一般化周期倍増
    - :nsns 周期軌道の二重ネイマーク-サッカー
    - :ch シェンチナー分岐の周期軌道
     デフォルト: :none
    ```
  * `idx::Int64`: 分岐が発生する `br.branch` または `br.eig` のインデックス（[`ContResult`](@ref)を参照）。デフォルト: 0
  * `param::Any`: 特別な点でのパラメータ値（これは推定値です）。デフォルト: 0.0
  * `norm::Any`: 特別な点での平衡のノルム デフォルト: 0.0
  * `printsol::Any`: `printsol = record_from_solution(x, param)` ここで `record_from_solution` は [`continuation`](@ref) の引数の1つです デフォルト: 0.0
  * `x::Any`: 特別な点での平衡 デフォルト: Vector{T}(undef, 0)
  * `τ::BifurcationKit.BorderedArray{Tvτ, T} where {T, Tvτ}`: 特別な点での分岐に沿った接線 デフォルト: BorderedArray(x, T(0))
  * `ind_ev::Int64`: 特別な点を検出するために責任を持つ固有値インデックス（該当する場合） デフォルト: 0
  * `step::Int64`: 特別な点が発生する連続ステップ デフォルト: 0
  * `status::Symbol`: `status ∈ {:converged, :guess, :guessL}` は、二分法アルゴリズムが特別な（分岐）点を検出するのに成功したかどうかを示します。`status == :guess` の場合、二分法アルゴリズムは `::ContinuationPar` に与えられた要件を満たすことができませんでした。`status == :guessL` も同様ですが、二分法アルゴリズムは分岐点の左側で停止しました。デフォルト: :guess
  * `δ::Tuple{Int64, Int64}`: `δ = (δr, δi)` ここで δr は不安定な固有値の数の変化を示し、δi は非ゼロの虚部を持つ不安定な固有値の数の変化を示します。したがって、`abs(δr)` は特別な（分岐）点でのヤコビ行列のカーネルの次元の推定値です。デフォルト: (0, 0)
  * `precision::Any`: 特別な点の位置の精度 デフォルト: -1
  * `interval::Tuple{T, T} where T`: 特別な点を含む区間パラメータ デフォルト: (0, 0)

```
