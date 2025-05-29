```
DPModel{T<:AbstractFloat, M, CT, SB<:AbstractVector{T}, S<:AbstractVector{T}} <: AbstractNLPModel{T, S}
```

最適化問題のための双対視点モデルで、KL正則化最小二乗機能を持つ`AbstractNLPModel`を拡張します。

# フィールド

  * `A::M`: 線形系を定義する制約行列
  * `b::SB`: 線形系Ax ≈ bにおけるターゲットベクトル
  * `c::S`: 目的関数のコストベクトル（デフォルトは1のベクトル）
  * `q::S`: KLダイバージェンス項のための事前分布ベクトル（デフォルトは一様分布1/n）
  * `λ::T`: KL項の強さを制御する正則化パラメータ（デフォルト: √eps）
  * `C::CT`: 線形系のための正定値スケーリング行列（デフォルト: 単位行列）
  * `mbuf::S`: 内部計算のための最初のm次元バッファ
  * `mbuf2::S`: 内部計算のための2番目のm次元バッファ
  * `nbuf::S`: 内部計算のためのn次元バッファ
  * `bNrm::T`: スケーリング目的のためのベクトルbのキャッシュされたノルム
  * `scale::T`: 問題のスケーリングファクター（デフォルト: 1.0）
  * `lse::LogExpFunction`: KLダイバージェンスを計算するための対数和指数関数
  * `name::String`: 問題インスタンスのためのオプションの識別子
  * `meta::NLPModelMeta{T,S}`: NLPModelsインターフェースに必要な問題メタデータ
  * `counters::Counters`: 操作追跡のためのパフォーマンスカウンタ

# パラメータ

  * `T`: 数値計算のための浮動小数点型
  * `M`: 制約行列のための行列型、AbstractMatrixのサブタイプでなければならない
  * `CT`: スケーリング行列の型
  * `SB`: 右辺のためのベクトル型、AbstractVector{T}のサブタイプでなければならない
  * `S`: 解とワークスペースベクトルのためのベクトル型、AbstractVector{T}のサブタイプでなければならない

# 例

```julia
# シンプルな双対視点モデルを作成
A = randn(10, 5)
b = randn(10)
model = DPModel(A=A, b=b)

# カスタム正則化を持つモデルを作成
model = DPModel(A=A, b=b, λ=1e-3)

# 簡略化されたモデル作成:
model = DPModel(A, b)
```
