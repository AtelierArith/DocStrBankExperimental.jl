```
SpecialEuclideanGroup{T}
```

特別ユークリッド群 $\mathrm{SE}(n) = \mathrm{SO}(n) ⋉ \mathcal T(n)$ は、[`SpecialOrthogonalGroup`](@ref) と [`TranslationGroup`](@ref) の [`LeftSemidirectProductGroupOperation`](@ref) からなるリー群であり、[`GroupOperationAction`](@ref)`{`[`LeftGroupOperationAction`](@ref)`}` とともに構成されます。

正確には、群演算は $\mathrm{SO}(n) ⋉ \mathcal T(n)$ 上で次のように定義されます：

$$
(r_1, t_1) ⋅ (r_2, t_2) = (r_1∘r_2, t_1 + r_1⋅t_2),
$$

ここで $r_1,r_2 ∈ \mathrm{SO}(n)$ および $t_1,t_2 ∈ \mathcal T(n)$ です。

同様に、$\mathrm{SO}(n) ⋊ \mathcal T(n)$ の要素については次のように書くことができます：

$$
(t_1, r_1) ⋅ (t_2, r_2) = (t_1 + r_1⋅s_2, r_1∘r_2)
$$

これらの両方のケースは、[アフィン形式](https://en.wikipedia.org/wiki/Affine_group#Matrix_representation)で単一の行列で表すことができます：

$$
g = \begin{pmatrix} r & t\\ \mathbf{0}_n^{\mathrm{T}} & 1\end{pmatrix},
\qquad r ∈ \mathrm{SO}(n), t ∈ \mathcal T(n),
$$

ここで $\mathbf{0}_n ∈ ℝ^n$ はゼロを含むベクトルを示します。

一般に、$\mathrm{SE}(n)$ の要素を $g$ と呼び、その回転成分と平行移動成分をそれぞれ $r$ と $t$ と呼びます。

# コンストラクタ

```
SpecialEuclideanGroup(n::Int; variant=:left, kwargs...)
SpecialOrthogonalGroup(n; kwargs...) ⋉ TranslationGroup(n; kwargs...)
TranslationGroup(n; kwargs...) ⋊ SpecialOrthogonalGroup(n; kwargs...)
```

特別ユークリッド群 $\mathrm{SE}(n) = \mathrm{SO}(n) ⋉ \mathcal T(n)$ を生成します。最初のコンストラクタは二番目のコンストラクタと同等です。

`kwargs...` のすべてのキーワード引数は、[`Rotations`](@extref `Manifolds.Rotations`) にも渡されます。

$$
\mathrm{SE}(n)
$$

のデフォルト表現はアフィン形式です。あるいは、`ArrayPartition` を使用して $(r,t)$ 上で作業することもできます。あるいは、$\mathcal T(n) ⋊ \mathrm{SO}(n)$ の場合は、`ArrayPartition` の $(t,r)$ を使用します。これは、最初のコンストラクタで `variant=:right` を設定することに対応します。
