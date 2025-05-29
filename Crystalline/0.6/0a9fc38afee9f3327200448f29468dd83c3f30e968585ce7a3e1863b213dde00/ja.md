```julia
calc_topology(
    n::AbstractVector{<:Integer},
    F::Crystalline.SmithNormalForm.Smith;
    allow_incompatible,
    allow_negative
) -> Crystalline.TopologyKind

```

対称ベクトル `n` が対称性の観点から自明または非自明なバンド結合であるかどうか、すなわち、基本バンド表現（EBR）基底における整数係数展開が存在するかどうか（すなわち、有理係数展開が存在するかどうか）を返します。[`TopologyKind`](@ref)（`TRIVIAL` または `NONTRIVIAL`）からの値を返します。

脆弱な対称ベクトルと自明な対称ベクトルの区別はありません。すなわち、`TRIVIAL` の返り値は、より注意深い検査によって実際には `FRAGILE` 状態である可能性があります。このような区別は、[SymmetryBases.jl](https://github.com/thchr/SymmetryBases.jl) の `calc_detailed_topology` によって行うことができます。

非自明な対称ベクトルの関連する対称指標を取得するには、[`symmetry_indicators`](@ref) も参照してください。

## 入力

EBR基底は `::BandRepSet`、`::Matrix{<:Integer}`、または `Smith` 分解として提供できます。`n` の長さは、EBR基底の不変表現の数と等しいか、不変表現の数に1を加えたものでなければなりません（すなわち、バンド接続を含む）。

## 実装

EBR行列 $\mathbf{B} = \mathbf{S}\boldsymbol{\Lambda}\mathbf{T}$ のスミス正規分解を通じて、整数係数展開が存在するかどうかを確認します。もし

$$
    (\mathbf{S}^{-1}\mathbf{n})_j = 0 \mod \lambda_j
$$

がすべての $j = 1, \ldots, d^{\text{bs}}$ に対して成り立つならば、整数係数 $c_j \in \mathbb{Z}$ を持つ $\mathbf{B}\mathbf{c} = \mathbf{n}$ の解が存在します。

## キーワード引数

`n` が互換性のあるバンド構造でない場合（すなわち、`iscompatible(n, [...]) = false` の場合）、エラーが発生します。この動作は、2つのブール型キーワード引数によって制御できます。

  * `allow_incompatible` (`false`): `true` の場合、互換性チェックを完全に無効にします。
  * `allow_negative` (`false`): `true` の場合、負の対称内容を許可しますが、`n` が代数的な意味で互換性関係を尊重する必要があることは維持します。
