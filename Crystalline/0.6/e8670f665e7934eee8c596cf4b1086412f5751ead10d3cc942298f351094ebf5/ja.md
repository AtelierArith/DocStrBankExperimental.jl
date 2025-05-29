```julia
symmetry_indicators(
    n::AbstractVector{<:Integer},
    F::Crystalline.SmithNormalForm.Smith;
    allow_incompatible,
    allow_negative
) -> Any

```

対称ベクトル `n` の対称指標インデックスを、`Collection{<:NewBandRep}`、`BandRepSet`、`Matrix{<:Integer}`、またはそのスミス分解として提供される一連の基本バンド表現（EBR） `brs` の文脈で返します。

詳細には、このメソッドは、EBR基底の対称指標群（参照、[`indicator_group`](@ref)） $[\lambda_1, \ldots, \lambda_n]$ に関連する非自明なインデックス $[\nu_1, \ldots, \nu_n]$ を返します。インデックス $\nu_i$ は、順序 $\lambda_i$ の循環群の要素であり、すなわち $\nu_i ∈ \mathbb{Z}_{\lambda_i} = \{0, 1, \ldots, \lambda_i-1\}$ です。

任意の対称指標が非ゼロであるかどうか（すなわち、対称ベクトルが位相的に非自明であるかどうか）を判断するには、`calc_topology` も参照してください。

## 実装

インデックスは、EBR行列 $\mathbf{B}$ のスミス正規分解 $\mathbf{B} = \mathbf{S} \boldsymbol{\Lambda}\mathbf{T}$ を使用して計算されます。具体的には、$\mathbf{s}_i^{-1}$ を $\mathbf{S}^{-1}$ の $i$ 番目の非自明な行とすると、対称ベクトル $\mathbf{n}$ の対称指標位相インデックスは $\nu_i = \mathbf{s}_i^{-1}\mathbf{n}$ として計算されます。[^\text{HCP}]

[^HCP]: [H.C. Po, J. Phys. Cond. Matter **32**, 263001 (2020)](https://doi.org/10.1088/1361-648X/ab7adb).

## キーワード引数

`n` が互換性のあるバンド構造でない場合（すなわち、`iscompatible(n, brs) = false` の場合）、エラーが発生します。この動作は、2つのブール型キーワード引数によって制御できます。

  * `allow_incompatible` (`false`): `true` の場合、互換性チェックを完全に無効にします。
  * `allow_negative` (`false`): `true` の場合、負の対称内容を許可しますが、`n` が代数的な意味で互換性関係を尊重する必要があることは維持します。
