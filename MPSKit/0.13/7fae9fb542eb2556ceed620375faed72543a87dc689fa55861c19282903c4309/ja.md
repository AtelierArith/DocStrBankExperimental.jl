```
FiniteMPS{A<:GenericMPSTensor,B<:MPSBondTensor} <: AbstractFiniteMPS
```

有限行列積状態を表す型です。

## プロパティ

  * `AL` – 左側ゲージされたMPSテンソル
  * `AR` – 右側ゲージされたMPSテンソル
  * `AC` – 中央ゲージされたMPSテンソル
  * `C` – ゲージテンソル
  * `center` – ゲージ中心の位置

centerプロパティは、MPS中心の位置を示す`center::HalfInt`を返します：

  * `isinteger(center)` → `center`は整数であり、基礎となる`ψ.ACs`フィールドに存在する最初の`AC`テンソルの位置を示します。
  * `ishalfodd(center)` → `center`は半奇数整数であり、`AC`テンソルが存在せず、ボンドテンソルがどのサイトの間にあるかを示します。

例えば、`mps.center = 7/2`は、ボンドテンソルが3番目のサイトの右側にあり、`mps.C[3]`を介してアクセスできることを意味します。

## 注意事項

慣例として、次のようになります：

  * `AL[i] * C[i]` = `AC[i]` = `C[i-1] * AR[i]`
  * `AL[i]' * AL[i] = 1`
  * `AR[i] * AR[i]' = 1`

---

## コンストラクタ

```
FiniteMPS([f, eltype], physicalspaces::Vector{<:Union{S,CompositeSpace{S}}},
          maxvirtualspaces::Union{S,Vector{S}};
          normalize=true, left=oneunit(S), right=oneunit(S)) where {S<:ElementarySpace}
FiniteMPS([f, eltype], N::Int, physicalspace::Union{S,CompositeSpace{S}},
          maxvirtualspaces::Union{S,Vector{S}};
          normalize=true, left=oneunit(S), right=oneunit(S)) where {S<:ElementarySpace}
FiniteMPS(As::Vector{<:GenericMPSTensor}; normalize=false, overwrite=false)
```

物理空間と仮想空間の仕様、またはテンソルのリスト`As`からMPSを構築します。すべてのケースは後者に還元されます。特に、非自明な全電荷を持つ状態は、`left`または`right`の仮想空間として非自明に電荷を持つベクトル空間を渡すことによって構築できます。

### 引数

  * `As::Vector{<:GenericMPSTensor}`: サイトテンソルのベクトル
  * `f::Function=rand`: テンソルデータの初期化関数
  * `eltype::Type{<:Number}=ComplexF64`: テンソルのスカラー型
  * `physicalspaces::Vector{<:Union{S, CompositeSpace{S}}`: 物理空間のリスト
  * `N::Int`: サイトの数
  * `physicalspace::Union{S,CompositeSpace{S}}`: ローカル物理空間
  * `virtualspaces::Vector{<:Union{S, CompositeSpace{S}}`: 仮想空間のリスト
  * `maxvirtualspace::S`: 最大仮想空間

### キーワード

  * `normalize=true`: 構築された状態を正規化する
  * `overwrite=false`: 与えられた入力テンソルを上書きする
  * `left=oneunit(S)`: 最も左の仮想空間
  * `right=oneunit(S)`: 最も右の仮想空間
