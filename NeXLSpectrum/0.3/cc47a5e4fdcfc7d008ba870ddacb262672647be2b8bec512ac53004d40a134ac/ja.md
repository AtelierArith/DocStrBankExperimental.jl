```
similarity(s1::Spectrum{T}, s2::Spectrum{T}, chs)::Float64 where {T<:Real}
similarity(specs::AbstractArray{Spectrum{T}}, chs)::Vector{Float64}
similarity(specs::AbstractArray{Spectrum}, minE::Float64=100.0)::Vector{Float64}
similarity(specs::AbstractArray{<:Spectrum}, det::Detector, elm::Element)::Vector{Float64}
similarity(specs::AbstractArray{Spectrum{T}}, det::Detector, mat::Material)::Vector{Float64}
```

i番目の`Spectrum`が他のスペクトルにどれだけ似ているかを測定する類似性メトリックのベクトルを返します。平均減少χ²統計メトリックは、`s1`と`s2`がカウント統計のみで異なる場合、メトリックはほぼ1になります。`s1`と`s2`がプローブ電流のドリフト、サンプルの不均一性、表面の粗さ、またはその他のカウント統計に関連しない理由で変動する場合、メトリックは1より大きくなります。

最初のバージョンは、minEと名目ビームエネルギーの間のすべてのチャネルをカバーします。3番目と4番目のバージョンは、`Detector`上の`Material`または`Element`からのスペクトルのピークを表すチャネルを考慮します。
