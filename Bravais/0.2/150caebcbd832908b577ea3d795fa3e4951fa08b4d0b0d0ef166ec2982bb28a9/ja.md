```
primitivebasismatrix(cntr::Char, ::Val{D}=Val(3)) --> SMatrix{D,D,Float64}
primitivebasismatrix(cntr::Char, ::Val{D}, ::Val{P}) --> SMatrix{D,D,Float64}
```

変換行列 $\mathbf{P}$ を返します。これは、中心 `cntr` を持つ従来の単位セルを、CDML 設定における対応する原始単位セル（次元 `D` および 周期性 `P`）に変換します。

`P` が提供されていない場合、デフォルトで `D` になります（例えば、Crystalline.jl の `spacegroup` に適用されるように）。`D` と `P` が異なる場合、部分周期群設定が仮定されます（例えば、Crystalline.jl の `subperiodicgroup` に適用されるように）。

## 直接空間と逆空間における変換

### 基底

返される変換行列 $\mathbf{P}$ は、直接空間の従来の基底 $(\mathbf{a}\ \mathbf{b}\ \mathbf{c})$ を直接空間の原始基底に変換します。

$$
    (\mathbf{a}'\ \mathbf{b}'\ \mathbf{c}') =
    (\mathbf{a}\ \mathbf{b}\ \mathbf{c})\mathbf{P}.
$$

同様に、$\mathbf{P}$ は逆空間の従来の基底 $(\mathbf{a}^*\ \mathbf{b}^*\ \mathbf{c}^*)$ を次のように変換します。

$$
(\mathbf{a}^{*\prime}\ \mathbf{b}^{*\prime}\ \mathbf{c}^{*\prime}) =
(\mathbf{a}^*\ \mathbf{b}^*\ \mathbf{c}^*)(\mathbf{P}^{-1})^{\text{T}}.
$$

[`transform(::DirectBasis, ::AbstractMatrix{<:Real})`](@ref) および [`transform(::ReciprocalBasis, ::AbstractMatrix{<:Real})`](@ref) も参照してください。

### 座標

直接空間または逆空間のいずれかの点の座標は、基底に関連して $\mathbf{P}$ の下で変換されます。具体的には、直接空間および逆空間の従来の点 $\mathbf{r} = (r_1, r_2, r_3)^{\text{T}}$ および $\mathbf{k} = (k_1, k_2, k_3)^{\text{T}}$ は、それぞれ、次のように原始設定に変換されます。

$$
\mathbf{r}' = \mathbf{P}^{-1}\mathbf{r},\\
\mathbf{k}' = \mathbf{P}^{\text{T}}\mathbf{k}.
$$

[`transform(::DirectPoint, ::AbstractMatrix{<:Real})`](@ref) および [`transform(::ReciprocalPoint, ::AbstractMatrix{<:Real})`](@ref) も参照してください。

## 設定の慣習

返される $\mathbf{P}$ によって示される原始セルの設定選択は、広く採用されている Cracknell-Davies-Miller-Love (CDML) 慣習に従います。[^\CDML] この慣習は、例えば [^\Aroyo] の表 2 で詳述されており（または、代わりに [^\ITB2] の表 1.5.4.1 および 1.5.4.2 から推測できます）、ビルバオ結晶学サーバー [^\BCS]、CDML の空間群の不変表現に関する参考文献 [^\CDML]、および C ライブラリ `spglib` [^\spglib] で採用されています。

この設定選択は、しばしば「ITA 原始設定」と呼ばれるものとは異なり、hP、hR、および oA ブラベータイプに対して異なります。

設定選択は通常、CDML 原始設定と呼ばれ、または、あまり頻繁ではなく、より曖昧に、結晶学的原始設定と呼ばれます。

[^CDML]: Cracknell, Davies, Miller, & Love, Kroenecker Product Tables, Vol. 1 (1979).

[^BCS]: ビルバオ結晶学サーバー, [KVEC](https://www.cryst.ehu.es/cryst/get_kvec.html).

[^Aroyo]: Aroyo *et al.*, [Acta Cryst. A70, 126 (2014)](https://doi.org/10.1107/S205327331303091X): 表 2 は $(\mathbf{P}^{-1})^{\text{T}}$ を示します。

[^ITB2]: Hahn, International Tables of Crystallography, Vol. B, 2nd edition (2001).

[^spglib]: Spglib ドキュメント: [原始設定への変換](https://spglib.github.io/spglib/definition.html#transformation-to-the-primitive-cell)。したがって、Bravais.jl および [Spglib.jl](https://github.com/singularitti/Spglib.jl) は同一の原始設定に変換され、相互に互換性があります。
