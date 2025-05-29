```
createLeafOpticalStruct(λ_bnds)

葉の色素（およびその他）の吸収断面積のPROSPECT-PROデータベースを読み込み、スペクトル単位が付加された[`LeafOpticalProperties`](@ref)型の構造体を返します。
```

# 引数

```
- `λ_bnds` 吸収断面積を平均化する上限と下限を定義する配列（スペクトルグリッド単位の有無にかかわらず）
```

# 例

```julia-repl
julia> using Unitful                                                               # Unitfulパッケージを含める必要があります
julia> opti = createLeafOpticalStruct((400.0:5:2400)*u"nm");                       # nm単位
julia> opti = createLeafOpticalStruct((0.4:0.1:2.4)*u"μm");                        # μm単位
julia> opti = CanopyOptics.createLeafOpticalStruct((10000.0:100:25000.0)u"1/cm");  # 波数単位 (cm⁻¹)
```
