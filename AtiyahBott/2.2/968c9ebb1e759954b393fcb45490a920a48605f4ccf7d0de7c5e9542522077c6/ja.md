```
R1(k)
```

$$
\mathcal{O}_{\mathbb{P}^n}(-k)
$$

のプルバックの第一導来関手の同変類。

# 引数

  * `k::Int64`: 正の整数。

# 例

$$
\begin{aligned}
\int_{\overline{M}_{0,0}(\mathbb{P}^{1},d)}\mathrm{c_{top}}(R^{1}\delta_{*}(\mathrm{ev}^{*}\mathcal{O}_{\mathbb{P}^{3}}(-1)))^2 &= \frac{1}{d^3} \\
\end{aligned}
$$

は次のように計算できます。

```jldoctest; setup = :(using AtiyahBott)
julia> d = 1; #他のdの値の場合はこの行を変更してください

julia> P = R1(1)^2;

julia> AtiyahBottFormula(1, d, 0, P, show_bar=false);
Result: 1
```

!!! warning "注意!"
    `k`が正でない場合、プログラムは停止します。

