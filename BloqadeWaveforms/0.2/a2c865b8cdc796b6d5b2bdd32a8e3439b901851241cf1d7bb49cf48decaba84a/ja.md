```
smooth(kernel, Xi::Vector, Yi::Vector, kernel_radius::Real)
```

カーネルスムーザー関数は、加重移動平均法を用いています。詳細は[カーネルスムーザー](https://en.wikipedia.org/wiki/Kernel_smoother)を参照してください。

# 理論

カーネル関数スムーシングは、隣接する点の加重平均を用いて、離散点の集合から滑らかな関数 $f: \mathcal{R}^p → \mathbf{R}$ を定義する技術です。これは次の方程式で表すことができます。

$$
Ŷ(X) = \sum_i K(X, X_i) Y_i / \sum_i K(X, X_i)
$$

ここで、$Ŷ(X)$ は既知のデータポイント $X_i$ と $Y_i$ の移動平均を計算することによって得られる滑らかな関数です。`K` はカーネル関数であり、$K(\frac{||X - X_i||}{h_λ})$ はユークリッドノルム $||X - X_i||$ が増加するにつれて減少します。$h_λ$ はカーネルの半径を制御するパラメータです。

# 利用可能なカーネル

次のカーネル関数は[`Kernels`](@ref)モジュールを介して利用可能です：

[`Kernels.biweight`](@ref); [`Kernels.cosine`](@ref); [`Kernels.gaussian`](@ref); [`Kernels.logistic`](@ref); [`Kernels.parabolic`](@ref); [`Kernels.sigmoid`](@ref); [`Kernels.triangle`](@ref); [`Kernels.tricube`](@ref); [`Kernels.triweight`](@ref); [`Kernels.uniform`](@ref)

# 引数

  * `kernel`: メソッド `kernel(t::Real)` を持つJulia関数。
  * `Xi::Vector`: 入力のリスト `X_i`。
  * `Yi::Vector`: 出力のリスト `Y_i`。
  * `kernel_radius::Real`: カーネルの半径。
