スカラー `x` におけるチェビシェフ多項式の `order` の二次導関数を計算します。`x` は [1.0,-1.0] の範囲内でなければなりません。2次元配列を返します。多項式の要素型は `x` の要素型によって決まります。

# シグネチャ

P = chebyshev*polynomial*sec_deriv(order,x)

# 例

```
julia> P = chebyshev_polynomial_sec_deriv(3,0.6)
[0.0  0.0  4.0  14.4]
```
