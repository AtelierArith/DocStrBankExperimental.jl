```
fit!(model::HiddenMarkovModel, Y::Matrix{<:Real}, X::Union{Matrix{<:Real}, Nothing}=nothing; max_iters::Int=100, tol::Float64=1e-6)
```

隠れマルコフモデルをEMアルゴリズムを使用して複数の試行データにフィットさせます。

# 引数

  * `model::HiddenMarkovModel`: フィットさせる隠れマルコフモデル。
  * `Y::Vector{<:Matrix{<:Real}}`: 試行されたエミッションデータ。
  * `X::Union{Vector{<:Matrix{<:Real}}, Nothing}=nothing`: スイッチング回帰モデルのフィッティングのためのオプションの入力データ
  * `max_iters::Int=100`: EMアルゴリズムを実行する最大反復回数。
  * `tol::Float64=1e-6`: 対数尤度がこの値未満で改善されると、アルゴリズムは停止します。
