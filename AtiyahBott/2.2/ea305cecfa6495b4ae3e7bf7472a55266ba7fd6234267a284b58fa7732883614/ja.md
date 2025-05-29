```
O1()
```

全評価マップの積に関する $\mathcal{O}_{\mathbb{P}^n}(1)$ のプルバックの同変類。

この関数は、`O1_i(j)` の積に相当し、ここで `j` はマークの数まで1から走ります。

# 例

以下のグロモフ-ウィッテン不変量

$$
\begin{aligned}
\int_{\overline{M}_{0,8}(\mathbb{P}^{2},3)}\prod_{i=1}^{8}\mathrm{ev}_{i}^{*}\mathcal{O}_{\mathbb{P}^{2}}(1)^2 &= 12 \\
\int_{\overline{M}_{0,1}(\mathbb{P}^{3},2)}\mathrm{ev}_{1}^{*}\mathcal{O}_{\mathbb{P}^{3}}(1)^2\cdot\mathrm{c_{top}}(\delta_{*}(\mathrm{ev}^{*}\mathcal{O}_{\mathbb{P}^{3}}(3))) &= 81 \\
\end{aligned}
$$

は次のように計算できます。

```jldoctest; setup = :(using AtiyahBott)
julia> P = O1()^2;

julia> AtiyahBottFormula(2, 3, 8, P, show_bar=false);
Result: 12

julia> P = O1()^2*Hypersurface(3);

julia> AtiyahBottFormula(3, 2, 1, P, show_bar=false);
Result: 81
```

ある `j` に対して `O1_i(j)` を除去するには、その関数で割るだけで十分です。

# 例

```julia-repl
julia> P = O1()//O1_i(1);
```

ここで `P` は、`j` が2から `m` まで走るすべての `O1_i(j)` の積です。
