```
fit!(model::HiddenMarkovModel, Y::Matrix{<:Real}, X::Union{Matrix{<:Real}, Nothing}=nothing; max_iters::Int=100, tol::Float64=1e-6)
```

EMアルゴリズムを使用して隠れマルコフモデルをフィットします。

# 引数

  * `model::HiddenMarkovModel`: フィットする隠れマルコフモデル。
  * `Y::Matrix{<:Real}`: エミッションデータ。
  * `X::Union{Matrix{<:Real}, Nothing}=nothing`: スイッチング回帰モデルのフィッティングのためのオプションの入力データ
  * `max_iters::Int=100`: EMアルゴリズムを実行する最大反復回数。
  * `tol::Float64=1e-6`: 対数尤度がこの値未満で改善される場合、アルゴリズムは停止します。
