```
monomial_to_newton!(P::Vector{T}, roots::Vector{T}) where T <: RingElement
```

多項式 $p$ を、標準モノミアル基底で与えられた係数の配列から、根 $r_0, r_1, \ldots, r_{n-2}$ のためのニュートン基底にインプレースで変換します。言い換えれば、出力係数 $c_i$ を決定し、$c_0 + c_1(x-r_0) + c_2(x-r_0)(x-r_1) + \ldots + c_{n-1}(x-r_0)(x-r_1)\cdots(x-r_{n-2})$ が入力多項式に等しくなるようにします。
