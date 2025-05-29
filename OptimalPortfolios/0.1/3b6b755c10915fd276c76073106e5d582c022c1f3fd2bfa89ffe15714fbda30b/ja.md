```
allocate(X, lower, upper; rf = 0.0, denoise = false, fullinvest = true,

method = "MSR")

与えられた方法に従って最適な%配分を計算します。

# 引数

  * `X::Matrix{Float64}`: N x T リターン行列、ここで N は資産の数、T はサンプルの数です。
  * `lower::Union{Float64, Vector{Float64}}`: %での配分の下限; スカラーとして指定された場合、すべての資産に同じ値が適用されます。
  * `upper::Union{Float64, Vector{Float64}}`: %での配分の上限; スカラーとして指定された場合、すべての資産に同じ値が適用されます。
  * `rf::Float64=0.0`: 無リスク金利; MSR メソッドにのみ適用されます。
  * `denoise::Bool=False`: 真の場合、サンプル共分散行列は、マルチェンコ-パスチュール分布から推定された λmax で固めることによってデノイズされます。
  * `fullinvest::Bool=True`: 真の場合、配分は1に合計されます。

%配分のベクトルを返します。
```
