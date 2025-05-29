```julia
iscompatible(
    n::AbstractVector{<:Integer},
    F::Crystalline.SmithNormalForm.Smith;
    allow_negative
) -> Any

```

対称ベクトル `n` が有効なバンドグルーピングであるかどうか、すなわちブリルアンゾーン内のすべての互換性関係を満たし、非負であるかどうかをテストします。つまり、`n` が物理バンド構造の集合 {BS} に属するかどうかをテストします。

このテストは、対称ベクトル `n` を、`BandRepSet`、`Collection{<:NewBandRep}`、`Matrix{<:Integer}`、または `Smith` 分解として提供された一連の基本バンド表現と比較します。`n` の不変表現のソートとこの一連の EBR が同一でなければなりません。

## キーワード引数

  * `allow_negative` (`false`): `true` の場合、負の対称内容を許可します。これは、`n` に負の内容が含まれているが、厳密な代数的意味で互換性関係を尊重する場合に関連する可能性があります。

## 実装

{BS} に属するかどうかは、一連の基本バンド表現 (EBR) と比較することでテストされます。対称ベクトル $\mathbf{n}$ は {BS} に属する場合、次の条件を満たします。

$$
    \tilde{\mathbf{S}}\tilde{\mathbf{S}}^{-1}\mathbf{n} = \mathbf{n}
$$

ここで、$\tilde{\mathbf{S}}$ ($\tilde{\mathbf{S}}^{-1}$) は、EBR 行列 $\mathbf{A} = \mathbf{S}\boldsymbol{\Lambda}\mathbf{T}$ のスミス正規分解における $\mathbf{S}$ ($\mathbf{S}^{-1}$) の非特異列 (行) を示します。

## 例

```julia-repl
julia> brs = calc_bandreps(22, Val(3)); # from Crystalline.jl
julia> n = parse(SymmetryVector, "Z₃, T₃, L₁, Y₃, Γ₃", irreps(brs)) # 互換性のあるベクトル

# 互換性のある対称ベクトルをテスト
julia> iscompatible(n, brs)
true

# 無効な対称ベクトルをテスト
julia> n′ = copy(n);
julia>  n′.multsv[1] .= [1,0,0,0]  # Z₃ を Z₁ に変更; 互換性のない修正
julia> iscompatible(n′, brs)
false

# 負の内容を持つ対称ベクトルをテスト
julia> n′′ = brs[1] + brs[2] - brs[3];  # 負の要素を含む
julia> iscompatible(n′′, brs)
false
julia> iscompatible(n′′, brs; allow_negative=true)
true
```
