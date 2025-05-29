```
InfiniteMPS{A<:GenericMPSTensor,B<:MPSBondTensor} <: AbtractMPS
```

無限マトリックス積状態を表す型。

## フィールド

  * `AL` – 左ゲージされたMPSテンソル
  * `AR` – 右ゲージされたMPSテンソル
  * `AC` – 中央ゲージされたMPSテンソル
  * `C` – ゲージテンソル

## 注意事項

慣例として、次のようになります：

  * `AL[i] * C[i]` = `AC[i]` = `C[i-1] * AR[i]`
  * `AL[i]' * AL[i] = 1`
  * `AR[i] * AR[i]' = 1`

---

## コンストラクタ

```
InfiniteMPS([f, eltype], physicalspaces::Vector{<:Union{S, CompositeSpace{S}},
            virtualspaces::Vector{<:Union{S, CompositeSpace{S}};
            kwargs...) where {S<:ElementarySpace}
InfiniteMPS(As::AbstractVector{<:GenericMPSTensor}; kwargs...)
InfiniteMPS(ALs::AbstractVector{<:GenericMPSTensor}, C₀::MPSBondTensor;
            kwargs...)
```

物理空間と仮想空間の仕様、またはテンソルのリスト`As`、または左ゲージされたテンソルのリスト`ALs`からMPSを構築します。

### 引数

  * `As::AbstractVector{<:GenericMPSTensor}`: サイトテンソルのベクトル
  * `ALs::AbstractVector{<:GenericMPSTensor}`: 左ゲージされたサイトテンソルのベクトル
  * `C₀::MPSBondTensor`: 初期ゲージテンソル
  * `f::Function=rand`: テンソルデータの初期化関数
  * `eltype::Type{<:Number}=ComplexF64`: テンソルのスカラー型
  * `physicalspaces::AbstractVector{<:Union{S, CompositeSpace{S}}`: 物理空間のリスト
  * `virtualspaces::AbstractVector{<:Union{S, CompositeSpace{S}}`: 仮想空間のリスト

### キーワード

  * `tol`: ゲージ固定の許容誤差
  * `maxiter`: ゲージ固定の最大反復回数
