```
Contact()
```

束のオイラー類の等変クラスは、忘却写像の下での$\mathrm{ev}^*\mathcal{O}_{\mathbb{P}^n}(2)$の直接画像と、忘却写像の双対化層のテンソルです。これは、奇数次元の射影空間における接触曲線をパラメータ化します。

# 例

$$
\begin{aligned}
\int_{\overline{M}_{0,2}(\mathbb{P}^{3},1)}\mathrm{ev}_{1}^{*}\mathcal{O}_{\mathbb{P}^{3}}(1)^{2}\cdot\mathrm{ev}_{2}^{*}\mathcal{O}_{\mathbb{P}^{3}}(1)^{3}\cdot\mathrm{c_{top}}(\delta_{*}(\omega_{\delta}\otimes\mathrm{ev}^{*}\mathcal{O}_{\mathbb{P}^{3}}(2))) &= 1 \\
\end{aligned}
$$

は次のように計算できます。

```jldoctest; setup = :(using AtiyahBott)
julia> P = O1_i(1)^2*O1_i(2)^3*Contact();

julia> AtiyahBottFormula(3, 1, 2, P, show_bar=false);
Result: 1
```
