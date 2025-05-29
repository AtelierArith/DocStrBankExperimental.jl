```
Jet(p, q)
```

エクイバリアントクラスのジェットバンドル $J^p$ は、$\mathcal{O}_{\mathbb{P}^n}(q)$ のプルバックに対する最初の $\psi$-クラスに関して定義されます。

# 引数

  * `p::Int64`: ジェットバンドルの指数。特に、これはランク $p+1$ のバンドルです。
  * `q::Int64`: プルバックされるラインバンドルの次数。

!!! note
    このバンドルを定義するためには、マークの数が少なくとも1でなければなりません。このバンドルをクラス `Psi(a)` で乗算することはできません。


# 例

$$
\begin{aligned}
\int_{\overline{M}_{0,1}(\mathbb{P}^{2},2)}\delta_{*}(\mathrm{ev}^{*}\mathcal{O}_{\mathbb{P}^{2}}(1)^{2})^{4}\cdot\mathrm{c_{top}}(J^{1}(\mathrm{ev}_{1}^{*}\mathcal{O}_{\mathbb{P}^{2}}(1))) &= 2 \\
\int_{\overline{M}_{0,1}(\mathbb{P}^{2},2)}\delta_{*}(\mathrm{ev}^{*}\mathcal{O}_{\mathbb{P}^{2}}(1)^{2})^{4}\cdot(\mathrm{c_{top}}(J^{1}(\mathrm{ev}_{1}^{*}\mathcal{O}_{\mathbb{P}^{2}}(1)))+\mathrm{ev}_{1}^{*}\mathcal{O}_{\mathbb{P}^{2}}(1)^{2}) &= 3 \\
\int_{\overline{M}_{0,1}(\mathbb{P}^{3},d)}\frac{\mathrm{ev}_{1}^{*}\mathcal{O}_{\mathbb{P}^{3}}(1)^{2}}{k}\cdot\mathrm{c_{top}}(J^{4d-2}(\mathrm{ev}_{1}^{*}\mathcal{O}_{\mathbb{P}^{3}}(k))) &= \frac{(4d-2)!}{(d!)^{4}} \\
\end{aligned}
$$

は次のように計算できます。

```jldoctest; setup = :(using AtiyahBott)
julia> P = Incidency(2)^4*Jet(1,1);

julia> AtiyahBottFormula(2, 2, 1, P, show_bar=false);
Result: 2

julia> P = Incidency(2)^4*(Jet(1,1)+O1()^2);

julia> AtiyahBottFormula(2, 2, 1, P, show_bar=false);
Result: 3

julia> d=1;k=1; #他の値の d の場合はこの行を変更してください

julia> P = (O1()^2)//k*Jet(4*d-2,k);

julia> AtiyahBottFormula(3, d, 1, P, show_bar=false);   #この積分の値は k には依存せず、d のみに依存します
Result: 2
```
