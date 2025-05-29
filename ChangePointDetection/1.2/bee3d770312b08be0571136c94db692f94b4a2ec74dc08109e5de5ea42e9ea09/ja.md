```
lsdd(x::Array{Float64,1}, y::Array{Float64,1}; folds = 5, sigma_list = nothing, lambda_list = nothing)
配列 `x` と `y` の最小二乗密度差 (lsdd) を計算します。
lsdd 値は、生成された 'x' と 'y' の確率密度がどれほど異なるかを特徴付けます。
lsdd が 0 に近いほど、確率密度はより類似しています。
入力 :
    'x', 'y' : lsdd 計算を行うデータの配列。
    folds : クロスバリデーションテストの数。高いほど精度が高いが、コストも高くなる。
    sigma_list, lambda_list : ガウスカーネルの最適化中にグリッドサーチを定義するポイント。
返り値 :
    L2 : lsdd 値。
```
