```julia
Gθ(
    pix::Krang.AbstractPixel,
    θs,
    isindir,
    n
) -> Tuple{Any, Any, Any, Any, Any, Bool}

```

$$
G_\theta=\int\frac{d\theta}{\sqrt{\Theta(\theta)}}
$$

の不定積分を返します。$\Theta(	heta)$の実装については[`θ_potential(x)`](@ref)を参照してください。

# 引数

  * `pix` : ピクセル情報
  * `θs` : 放射傾斜
  * `isindir` : パスは直接ですか、それとも間接ですか？
  * `n` : ミノタイムで順序付けられたn番目の画像
