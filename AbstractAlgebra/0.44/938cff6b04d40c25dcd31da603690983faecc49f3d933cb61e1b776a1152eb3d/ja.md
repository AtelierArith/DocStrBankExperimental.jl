```
newton_to_monomial!(P::Vector{T}, roots::Vector{T}) where T <: RingElement
```

多項式 $p$ を、根 $r_0, r_1, \ldots, r_{n-2}$ のニュートン基底で与えられた係数の配列から標準モノミアル基底にインプレースで変換します。言い換えれば、これは $c_0 + c_1(x-r_0) + c_2(x-r_0)(x-r_1) + \ldots + c_{n-1}(x-r_0)(x-r_1)\cdots(x-r_{n-2})$ を評価します。ここで、$c_i$ は入力係数 $p$ によって与えられます。
