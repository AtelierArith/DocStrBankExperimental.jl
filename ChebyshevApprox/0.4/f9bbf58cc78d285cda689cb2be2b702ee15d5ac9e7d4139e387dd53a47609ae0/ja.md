テンソル積チェビシェフ多項式の最初の導関数を、位置 `pos` の変数に関して、点 `x` で計算します。与えられた `weights`、多項式の `order`、および `domain` に基づいています。

# シグネチャ

d = chebyshev_derivative(weights,x,pos,order,domain)

# 例

```
julia> weights = [1.66416      0.598458    -0.0237052     0.00272941
  0.26378      0.0948592   -0.00375743    0.000432628
 -0.0246176   -0.00885287   0.000350667  -4.03756e-5
  0.00372291   0.00133882  -5.30312e-5    6.10598e-6]
julia> x = [5.5,0.9]
julia> ord = (3,3)
julia> dom = [9.0 1.5; 3.0 0.5]
julia> pos = 1
julia> d = chebyshev_derivative(weights,x,pos,ord,dom)
0.08487312307427555
```
