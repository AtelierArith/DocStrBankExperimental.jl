```
ConstantInterpolationIntInv(u, t, A)
```

これは`ConstantInterpolation`の積分の逆数の補間です。`invert_integral(A::ConstantInterpolation{<:AbstractVector{<:Number}})`を使って簡単に構築できます。

## 引数

  * `u` : `A.t`によって与えられます
  * `t` : `A.I`によって与えられます（`A`の累積積分）
  * `A` : `ConstantInterpolation`オブジェクト
