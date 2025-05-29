```
Hypersurface(b)
```

バンドルのオイラー類の等変クラスは、$\mathrm{ev}^*\mathcal{O}_{\mathbb{P}^n}(b)$の忘却写像による直接画像に等しい。これは、次数 `b` の超曲面に含まれる曲線をパラメータ化します。

# 引数

  * `b::Int64`: 超曲面の次数。あるいは、整数の配列であり、配列の各要素によって定義される等変クラスの積を意味します。

# 例

次のカルビ-ヤウ三重体のグロモフ-ウィッテン不変量

$$
\begin{aligned}
\int_{\overline{M}_{0,0}(\mathbb{P}^{4},1)}\mathrm{c_{top}}(\delta_{*}(\mathrm{ev}^{*}\mathcal{O}_{\mathbb{P}^{4}}(5))) &= 2875 \\
\int_{\overline{M}_{0,0}(\mathbb{P}^{5},2)}\mathrm{c_{top}}(\delta_{*}(\mathrm{ev}^{*}\mathcal{O}_{\mathbb{P}^{5}}(3))^{\oplus 2}) &= \frac{423549}{8} \\
\int_{\overline{M}_{0,0}(\mathbb{P}^{5},3)}\mathrm{c_{top}}(\delta_{*}(\mathrm{ev}^{*}\mathcal{O}_{\mathbb{P}^{5}}(4)))\cdot\mathrm{c_{top}}(\delta_{*}(\mathrm{ev}^{*}\mathcal{O}_{\mathbb{P}^{5}}(2))) &= \frac{422690816}{27} \\
\int_{\overline{M}_{0,0}(\mathbb{P}^{7},4)}\mathrm{c_{top}}(\delta_{*}(\mathrm{ev}^{*}\mathcal{O}_{\mathbb{P}^{7}}(2)))^4 &= 25705160 \\
\end{aligned}
$$

は次のように計算できます

```jldoctest; setup = :(using AtiyahBott)
julia> P = Hypersurface(5);

julia> AtiyahBottFormula(4, 1, 0, P, show_bar=false);
Result: 2875

julia> P = Hypersurface([3,3]);

julia> AtiyahBottFormula(5, 2, 0, P, show_bar=false);
Result: 423549//8

julia> P = Hypersurface(4)*Hypersurface(2);

julia> AtiyahBottFormula(5, 3, 0, P, show_bar=false);
Result: 422690816//27

julia> P = Hypersurface(2)^4;

julia> AtiyahBottFormula(7, 4, 0, P, show_bar=false);
Result: 25705160
```

!!! warning "注意!"
    `b` が正でない場合、プログラムは停止します。

