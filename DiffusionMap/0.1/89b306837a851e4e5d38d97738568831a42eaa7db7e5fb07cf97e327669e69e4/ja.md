```
diffusion_map(P, d; t=1)
diffusion_map(X, kernel, d; t=1)
```

拡散マップを計算します。

2つの呼び出しシグネチャ：

  * データ行列 `X` が渡されます。例は列にあります。
  * 右確率行列 `P` が渡されます。（例：事前計算されたカーネル行列の場合）

# 引数

  * `d`: 次元
  * `t`: ステップ数

# 例

```julia
# カーネルを定義
kernel(xᵢ, xⱼ) = gaussian_kernel(xᵢ, xⱼ, 0.5)

# データ行列（100データポイント、2Dベクトル）
X = rand(2, 100)

# 1Dへの拡散マップ
X̂ = diff_map(X, kernel, 1)
```
