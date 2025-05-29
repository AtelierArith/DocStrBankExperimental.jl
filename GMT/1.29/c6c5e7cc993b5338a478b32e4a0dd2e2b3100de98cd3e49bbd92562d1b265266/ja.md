```julia
lowess(x, y, span = 2 / 3, nsteps = 3, delta = 0.01 * (maximum(x) - minimum(x)))
```

`y`を`x`に対して散布図のスムーズを計算します。入力ベクトル`x`と`y`は整数または浮動小数点数を含む必要があります。パラメータ`span`と`delta`は型`T`でなければならず、`T <: AbstractFloat`です。ベクトル`ys`を返します；`ys[i]`は`x[i]`でのフィッティング値です。スムーズなプロットを得るには、`ys`を`x`に対してプロットする必要があります。

# 引数

  * `x::Vector`: 散布図上の点の横座標。`x`は順序付けられている必要があります。
  * `y::Vector`: 散布図上の点の縦座標。
  * `span`: スムージングの量。
  * `nsteps::Integer`: ロバストフィットの反復回数。
  * `delta`: 計算を節約するために使用できる非負のパラメータ。デフォルトは`0.01 * (maximum(x) - minimum(x))`です。

# 例

```julia
x = sort(10 .* rand(100))
y = sin.(x) .+ 0.5 * rand(100)
ys = lowess(x, y, span=0.2)
scatter(x, y)
plot!(x, ys)
```
