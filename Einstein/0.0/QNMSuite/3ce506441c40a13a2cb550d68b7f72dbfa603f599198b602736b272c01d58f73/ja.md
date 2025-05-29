```
continued_fraction_lentz([TF=Float64], a::Function, b::Function, tol::TF, min_iter::Integer, max_iter::Integer) where {TF<:AbstractFloat}
```

連分数を計算します。

$$
f(x)=b_0+\frac{a_1}{b_1+\frac{a_2}{b_2+\frac{a_3}{b_3+\frac{a_4}{b_4+\frac{a_5}{b_5+\cdots}}}}}
$$

修正されたレンツ法を使用します。[duetosymmetry/qnm](https://github.com/duetosymmetry/qnm)から翻訳されました。

# 引数

  * `a`: `aᵢ`項を返す関数。
  * `b`: `bᵢ`項を返す関数。
  * `tol`: 収束のための許容誤差。
  * `min_iter`: 実行する最小反復回数。
  * `max_iter`: 実行する最大反復回数。

# 戻り値

  * `fᵢ`: 連分数の値。
  * `errorᵢ`: 推定誤差。
  * `i`: 実行された反復回数。

# 例

## 連分数を使用して2の平方根を計算する

$$
\sqrt{2} = 1 + \frac{1}{2 + \frac{1}{2 + \frac{1}{2 + \frac{1}{2 + \cdots}}}} \approx 1.414213562373095
$$

```julia
a(i) = 1
b(i) = i == 0 ? 1 : 2
continued_fraction_lentz(Float64, a, b, 10*eps(Float64), 50, 1000)
```

## 黄金比を計算する

$$
\phi = 1 + \frac{1}{1 + \frac{1}{1 + \frac{1}{1 + \cdots}}} \approx 1.618033988749895
$$

```julia
a(i) = 1
b(i) = 1
continued_fraction_lentz(Float64, a, b, 10*eps(Float64), 50, 1000)
```

# 参考文献

  * [qnm/qnm/contfrac.py at master · duetosymmetry/qnm](https://github.com/duetosymmetry/qnm/blob/master/qnm/contfrac.py)
  * [press2007numerical, Stein:2019mop, lentz1976generating, thompson1986coulomb, DLMF*3103*online](@cite)

```
