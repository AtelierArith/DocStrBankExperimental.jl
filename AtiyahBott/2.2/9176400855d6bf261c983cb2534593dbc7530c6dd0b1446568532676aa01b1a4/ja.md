```
O1_i(j)
```

$$
j
$$

-番目の評価マップに関する$\mathcal{O}_{\mathbb{P}^n}(1)$のプルバックの同変類。

# 引数

  * `j::Int64`: 評価マップ。

# 例

次のグロモフ・ウィッテン不変量

$$
\begin{aligned}
\int_{\overline{M}_{0,2}(\mathbb{P}^{1},1)}\mathrm{ev}_{1}^{*}\mathcal{O}_{\mathbb{P}^{1}}(1)\cdot\mathrm{ev}_{2}^{*}\mathcal{O}_{\mathbb{P}^{1}}(1) &= 1 \\
\int_{\overline{M}_{0,1}(\mathbb{P}^{3},1)}\mathrm{ev}_{1}^{*}\mathcal{O}_{\mathbb{P}^{2}}(1)^{2}\cdot\mathrm{c_{top}}(\delta_{*}(\mathrm{ev}^{*}\mathcal{O}_{\mathbb{P}^{3}}(2))) &= 4
\end{aligned}
$$

は次のように計算できます。

```jldoctest; setup = :(using AtiyahBott)
julia> P = O1_i(1)*O1_i(2);

julia> AtiyahBottFormula(1, 1, 2, P, show_bar=false);
Result: 1

julia> P = O1_i(1)^2*Hypersurface(2);

julia> AtiyahBottFormula(3, 1, 1, P, show_bar=false);
Result: 4
```

!!! warning "注意!"
    `j`が1とマークの数の間でない場合、プログラムは停止します。

