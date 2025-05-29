```julia
fit!(
    m,
    X::Matrix{<:Real},
    Y::Matrix{<:Real};
    opt,
    batchsize,
    epochs,
    verbosity
) -> Tuple{Any, @NamedTuple{learning_curve::Vector{Float64}, best_epoch::Int64, best_loss::Float64}}

```

モデルをXとYで与えられたデータにフィットさせます。

# パラメータ

  * `m`: トレーニングされるモデル。
  * `X`: dが入力特徴の数、nがサンプルの数であるdxn行列。
  * `Y`: dが出力の次元、nがサンプルの数であるdxn行列。
  * `opt`: トレーニング中に使用する最適化アルゴリズム（デフォルト = Adam(1e-3)）。
  * `batchsize`: 勾配降下法の各イテレーションのバッチサイズ（デフォルト = 32）。
  * `epochs`: トレーニングするエポックの数（デフォルト = 100）。
  * `verbosity`: 進捗バーを表示するかどうか（デフォルト = 1）または表示しない（0）。
