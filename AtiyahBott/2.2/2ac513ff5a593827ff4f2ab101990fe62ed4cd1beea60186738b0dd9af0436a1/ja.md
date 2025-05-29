```
Incidency(r)
```

線形部分空間のコドメイン `r` を満たす曲線をパラメータ化するサイクルの同変類。

# 引数

  * `r::Int64`: サブバラエティのコドメイン。あるいは、配列の整数であり、配列の各要素によって定義される同変類の積を意味します。

# 例

次のグロモフ・ウィッテン不変量

$$
\begin{aligned}
\int_{\overline{M}_{0,0}(\mathbb{P}^{3},1)}\delta_{*}(\mathrm{ev}^{*}\mathcal{O}_{\mathbb{P}^{3}}(1)^{3})^{2} &= 1 \\
\int_{\overline{M}_{0,0}(\mathbb{P}^{3},1)}\delta_{*}(\mathrm{ev}^{*}\mathcal{O}_{\mathbb{P}^{3}}(1)^{2})^{2}\cdot \delta_{*}(\mathrm{ev}^{*}\mathcal{O}_{\mathbb{P}^{3}}(1)^{3}) &= 1 \\
\int_{\overline{M}_{0,0}(\mathbb{P}^{3},3)}\delta_{*}(\mathrm{ev}^{*}\mathcal{O}_{\mathbb{P}^{3}}(1)^{2})^{2}\cdot \mathrm{c_{top}}(\delta_{*}(\mathrm{ev}^{*}\mathcal{O}_{\mathbb{P}^{3}}(3))) &= 756 \\
\end{aligned}
$$

は次のように計算できます

```jldoctest; setup = :(using AtiyahBott)
julia> P = Incidency(3)^2;

julia> AtiyahBottFormula(3, 1, 0, P, show_bar=false);
Result: 1

julia> P = Incidency([2,2,3]);

julia> AtiyahBottFormula(3, 1, 0, P, show_bar=false);
Result: 1

julia> P = Incidency([2,2])*Hypersurface(3);

julia> AtiyahBottFormula(3, 3, 0, P, show_bar=false);
Result: 756
```

!!! warning "注意!"
    `r` が正でない場合、プログラムは停止します。

