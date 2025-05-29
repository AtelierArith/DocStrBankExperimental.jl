```
cheb_series_integrate(df::AbstractVector{TFC}) where {TFC<:Union{AbstractFloat,Complex{<:AbstractFloat}}}
cheb_series_integrate!(f::AbstractVector{TFC}, df::AbstractVector{TFC}) where {TFC<:Union{AbstractFloat,Complex{<:AbstractFloat}}}
```

関数 $f'(x)$ の不定積分を計算します。これはそのチェビシェフ級数が与えられ、積分定数は $f(-1) = 0$ となるように選ばれます。

# 数学的詳細

入力関数 $f'(x)$ が長さ $n$ のチェビシェフ級数で表される場合：

$$
f'(x) = \sum_{r=0}^{n-1} c_r T_r(x)
$$

その積分 $f(x)$ は長さ $n+1$ のチェビシェフ級数で表されます：

$$
f(x) = \sum_{r=0}^{n} b_r T_r(x)
$$

ここで：

  * $$
    b_0
    $$

    は積分定数から次のように決定されます：

$$
b_0 = \sum_{r=1}^{n} (-1)^{r+1} b_r
$$

  * 他の係数は次のように与えられます：

$$
b_1 = c_0 - c_2/2
b_r = (c_{r-1} - c_{r+1})/(2r) \text{ for } r > 1
$$

ここで $c_{n+1} = c_{n+2} = 0$ です。

# 引数

  * `df`: $f'$ のチェビシェフ級数係数のベクトル
  * `f`: $f$ のチェビシェフ級数係数のベクトル

# 参考文献

  * [chebfun/@chebtech/cumsum.m at master · chebfun/chebfun](https://github.com/chebfun/chebfun/blob/master/%40chebtech/cumsum.m)
