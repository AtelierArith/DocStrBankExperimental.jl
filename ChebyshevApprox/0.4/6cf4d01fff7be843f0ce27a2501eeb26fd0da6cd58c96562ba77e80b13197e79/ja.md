スカラー点 `x` での次数 `order` のチェビシェフ多項式を計算します。`x` は `dom` に含まれている必要があります。2次元配列を返します。多項式の要素型は `x` の要素型によって決まります。

# シグネチャ

P = chebyshev_polynomial(order,x,dom)

# 例

```
julia> P = chebyshev_polynomial(3,0.6,[1.0,-1.0])
[1.0  0.6  -0.28  -0.936]
```
