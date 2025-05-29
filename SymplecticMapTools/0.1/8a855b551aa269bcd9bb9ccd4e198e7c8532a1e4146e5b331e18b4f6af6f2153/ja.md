```
KernelLabel
```

コンストラクタ:

  * `KernelLabel(x::AbstractArray, c::AbstractVector, σ::Number;`               `kernel::Symbol=:SquaredExponential)`
  * `KernelLabel(x::AbstractArray, c::AbstractVector, σ::AbstractArray;`               `kernel::Symbol=:SquaredExponential)`

おおよそ不変なカーネルラベル関数。

コンストラクタ要素:

  * `x`: 補間点の `d` × `2N` 配列で、ここで `x[:, n+N] = F(x[:, n])` かつ `n<=N` であり、あるシンプレクティック写像 `F`。
  * `c`: カーネル関数の係数の長さ `2N` のベクトル
  * `σ`: カーネルの長さスケール（ベクトルの場合、異なる方向で長さスケールが異なる）
  * `kernel`: 使用されるカーネルのタイプ

現在サポートされているカーネルは次のとおりです:

  * `:SquaredExponential`: 二乗指数カーネル   K(x, y) = exp(-|x-y|²)
  * `:InverseMultiquadric`: β=1 逆多重二次カーネル   K(x, y) = (1+|x-y|²)^(-1/2)
  * `:FourierSE`: フーリエ × カルテジアン二乗指数カーネル   K(x, y) = exp(-sin²(x₁-y₁) - (x₂-y₂)²)
  * `:Fourier`: フーリエ × フーリエ二乗指数カーネル   K(x, y) = exp(-sin²(x₁-y₁) - sin²(x₂-y₂))
