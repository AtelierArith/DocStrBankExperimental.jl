```
KRatio(
    xray::CharXRay,
    unkProps::Dict{Symbol,<:Any},
    stdProps::Dict{Symbol,<:Any},
    standard::Material,
    kratio::AbstractFloat,
)
```

k-ratioは、未知の組成の材料と既知の組成の標準の2つの類似した強度測定の比率です。各測定には、測定を特徴付けるための:BeamEnergy (必須)、:TakeOffAngle (必須)、:Coating (オプション)などのプロパティがあります。最小限のプロパティセットには以下が含まれます：

プロパティ: (これらの`Symbol`は意図的にNeXLSpectrumで使用されているものと同じです)

```
:BeamEnergy 入射ビームエネルギー（eV単位）
:TakeOffAngle ラジアン単位
:Coating 導電性コーティングを詳細に記述したNeXLCore.FilmオブジェクトまたはFilm[]
```

一部のアルゴリズムでは追加のプロパティが必要な場合があります。

k-ratioは、単一元素からの特性X線（`CharXRay`）に関連付けられています。WDS k-ratioは通常、単一の`CharXRay`に関連付けられますが、EDS測定はエネルギーが類似した多くの`CharXRay`に関連付けられる場合があります。k-ratioは常に他の材料に対して相対的です。通常、この`Material`の組成はよく知られています。しかし、k-ratioが再標準化されると、中間材料があまり知られていない可能性があります。

メソッド：

```
> element(kr)
> xrays(kr)
> standard(kr)
> elms(KRatioBase[...])
> NeXLUncertainties.value(kr::KRatio)
> NeXLUncertainties.σ(kr::KRatio)
> nonnegk(kr::KRatio)
> Statistics.mean(krs::AbstractVector{KRatio})::UncertainValue
> Base.getindex(krs::AbstractVector{KRatio}, cxr::CharXRay)
> strip(krs::AbstractVector{KRatio}, els::Element...)::Vector{KRatio}
> asa(::Type{DataFrame}, krs::AbstractVector{KRatio})::DataFrame
```
