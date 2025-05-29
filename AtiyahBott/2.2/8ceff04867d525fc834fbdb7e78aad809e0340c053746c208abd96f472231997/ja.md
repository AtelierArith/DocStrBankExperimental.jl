```
Psi(a)
```

$$
\psi
$$

-クラスのサイクルの同変類。

# 引数

  * `a::Vector{Int64}`: $\psi$ クラスの指数のベクトル。これは順序付けられており、最初の要素は $\psi_1$ の指数、2 番目は $\psi_2$ の指数、というようになります。

!!! note
    `a` のサイズは最大で `m` でなければなりません。もしそれが小さい場合、欠落した指数はゼロと見なされます。もし `a` が数値であれば、それは $\psi_1$ の指数と見なされます。


!!! warning "注意!"
    次のいずれかの条件がある場合、プログラムは停止します：

      * `a` のサイズが `m` より大きい場合、
      * `a` に負の数が含まれている場合。


# 例

次のグロモフ-ウィッテン不変量

$$
\begin{aligned}
\int_{\overline{M}_{0,2}(\mathbb{P}^{6},2)}\mathrm{ev}_{1}^{*}\mathcal{O}_{\mathbb{P}^{6}}(1)^{5}\cdot\mathrm{ev}_{2}^{*}\mathcal{O}_{\mathbb{P}^{6}}(1)^{2}\cdot\mathrm{c_{top}}(\delta_{*}(\mathrm{ev}^{*}\mathcal{O}_{\mathbb{P}^{6}}(5)))\cdot\psi_{1}\psi_{2}^{0} &= 495000 \\
\int_{\overline{M}_{0,2}(\mathbb{P}^{10},2)}\mathrm{ev}_{1}^{*}\mathcal{O}_{\mathbb{P}^{10}}(1)^{8}\cdot\mathrm{ev}_{2}^{*}\mathcal{O}_{\mathbb{P}^{10}}(1)^{6}\cdot\mathrm{c_{top}}(\delta_{*}(\mathrm{ev}^{*}\mathcal{O}_{\mathbb{P}^{10}}(7)))\cdot\psi_{1}^{2} &= 71804533752 \\
\int_{\overline{M}_{0,1}(\mathbb{P}^{2},2)}\mathrm{ev}_{1}^{*}\mathcal{O}_{\mathbb{P}^{2}}(1)^{2}\cdot\psi_{1}^{4} &= \frac{1}{8} \\
\int_{\overline{M}_{0,1}(\mathbb{P}^{2},2)}\delta_{*}(\mathrm{ev}^{*}\mathcal{O}_{\mathbb{P}^{2}}(1)^{2})^{4}\cdot\mathrm{ev}_{1}^{*}\mathcal{O}_{\mathbb{P}^{2}}(1)\cdot(\mathrm{ev}_{1}^{*}\mathcal{O}_{\mathbb{P}^{2}}(1)+\psi_{1}) &= 2 \\
\int_{\overline{M}_{0,1}(\mathbb{P}^{3},2)}\mathrm{ev}_{1}^{*}\mathcal{O}_{\mathbb{P}^{2}}(1)\cdot(\psi_{1}^{7}\cdot\mathrm{ev}_{1}^{*}\mathcal{O}_{\mathbb{P}^{2}}(1)+\psi_{1}^{6}\cdot\mathrm{ev}_{1}^{*}\mathcal{O}_{\mathbb{P}^{2}}(1)^{2}) &= -\frac{5}{16} \\
\end{aligned}
$$

は次のように計算できます

```jldoctest; setup = :(using AtiyahBott)
julia> P = O1_i(1)^5*O1_i(2)^2*Hypersurface(5)*Psi([1,0]);

julia> AtiyahBottFormula(6, 2, 2, P, show_bar=false);
Result: 495000

julia> P = O1_i(1)^8*O1_i(2)^6*Hypersurface(7)*Psi(2);

julia> AtiyahBottFormula(10, 2, 2, P, show_bar=false);
Result: 71804533752

julia> P = O1()^2*Psi(4);

julia> AtiyahBottFormula(2, 2, 1, P, show_bar=false);
Result: 1//8

julia> P = Incidency(2)^4*O1_i(1)*(O1_i(1) + Psi(1));

julia> AtiyahBottFormula(2, 2, 1, P, show_bar=false); #4点を通り、直線に接する平面の二次曲線の数
Result: 2

julia> P = O1()*(Psi(7)*O1()+Psi(6)*O1()^2);

julia> AtiyahBottFormula(3, 2, 1, P, show_bar=false);
Result: -5//16
```

!!! warning "Psiは単一です！"
    `Psi` は自分自身と掛け算できません。

    ```julia-repl
    julia> P = O1()^2*Psi(1)^4;                  #これは**間違い**
    julia> AtiyahBottFormula(2,2,1,P);
    Warning: more instances of Psi has been found. Type:
    julia> ?Psi
    for support.
    julia> P = O1()^2*Psi(3)*Psi(1);             #これは**間違い**
    julia> AtiyahBottFormula(2,2,1,P);
    Warning: more instances of Psi has been found. Type:
    julia> ?Psi
    for support.
    julia> P = O1()^2*Psi(4);
    julia> AtiyahBottFormula(2,2,1,P);
    Result: 1//8
    ```

