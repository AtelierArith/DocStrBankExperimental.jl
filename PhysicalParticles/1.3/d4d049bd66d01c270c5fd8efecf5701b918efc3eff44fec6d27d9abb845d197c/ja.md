rotate(p::PVector, vec::PVector, θ::Number)

ベクトル `vec` の方向を中心に角度 `θ` だけ `p` を回転させます。

正規化された `vec = (x, y, z)` の場合、回転行列は次のようになります：

```
            |  cos(θ) + (1-cos(θ))*x^2   (1-cos(θ))*x*y - sin(θ)*z  (1-cos(θ))*x*z + sin(θ)*y |
M(vec, θ) = | (1-cos(θ))*y*x + sin(θ)*z   cos(θ) + (1-cos(θ))*y^2   (1-cos(θ))*y*z - sin(θ)*x |
            | (1-cos(θ))*z*x - sin(θ)*y  (1-cos(θ))*z*y + sin(θ)*x   cos(θ) + (1-cos(θ))*z^2  |
```
