`order`のチェビシェフ多項式の2階導関数をベクトル`x`の各点で計算します。`x`の要素は[1.0,-1.0]の範囲内でなければなりません。2次元配列を返します。多項式の要素型は`x`の要素型によって決まります。

# シグネチャ

P = chebyshev*polynomial*sec_deriv(order,x)

# 例

```
julia> P = chebyshev_polynomial_sec_deriv(3,[0.6,0.4])
[0.0  0.0  4.0  14.4
 0.0  0.0  4.0   9.6]
```
