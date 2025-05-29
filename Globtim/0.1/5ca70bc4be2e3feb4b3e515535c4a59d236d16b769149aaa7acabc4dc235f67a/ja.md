```
struct test_input
```

テストを実行するために必要なすべてのパラメータを含む構造体。

# フィールド

  * `dim::Int`: 問題空間の次元
  * `center::Vector{Float64}`: サンプリング領域の中心点
  * `GN::Union{Int, Nothing}`: サンプル数（オプション）
  * `prec::Union{Tuple{Float64,Float64}, Nothing}`: 精度パラメータ（α, δ）
  * `tolerance::Union{Float64, Nothing}`: 収束許容値
  * `noise::Union{Tuple{Float64,Float64}, Nothing}`: ノイズパラメータ
  * `sample_range::Union{Float64, Nothing}`: 中心周辺のサンプリング範囲
  * `reduce_samples::Union{Float64, Nothing}`: サンプルセットサイズの削減係数
  * `objective::Function`: 評価される目的関数

# コンストラクタ

```
test_input(f::Function; kwargs...)
```

# キーワード引数

  * `dim::Int=2`: 問題の次元
  * `center::AbstractVector{Float64}=fill(0.0, dim)`: 中心点
  * `alpha::Float64=0.1`: 最初の精度パラメータ
  * `delta::Float64=0.5`: 2番目の精度パラメータ
  * `tolerance::Float64=2e-3`: 収束許容値
  * `sample_range::Number=1.0`: 中心周辺のサンプリング範囲
  * `reduce_samples::Float64=1.0`: サンプル削減係数
  * `model=nothing`: 目的関数に渡されるオプションのモデルパラメータ
  * `outputs=nothing`: 目的関数に渡されるオプションの出力パラメータ
