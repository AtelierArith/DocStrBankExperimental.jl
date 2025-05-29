```
(sampled_masses, sampled_mags) =  generate_stars_mag(mini_vec::AbstractVector{<:Number}, mags, mag_names::AbstractVector{String}, absmag::Real, absmag_name::String, imf::Distributions.Sampleable{Distributions.Univariate,Distributions.Continuous}; dist_mod::Number=0, rng::AbstractRNG=default_rng(), mag_lim::Number=Inf, mag_lim_name::String="V", binary_model::StarFormationHistories.AbstractBinaryModel=RandomBinaryPairs(0.3))
```

提供された初期恒星質量 `mini_vec`、絶対光度 `mags`、およびフィルタ名 `mag_names` によって定義された等時線からモック恒星集団を生成します。この集団は、フィルタ `absmag_name::String`（例： "V" または "F606W"）において、合計絶対光度 `absmag::Real`（例： -7 または -12）までサンプリングされます。このフィルタは提供された `mag_names::AbstractVector{String}` に含まれています。他の引数は、主なドキュメントを含む [`generate_stars_mass`](@ref) と共有されています。

# 注意事項

## 集団の光度

固定の初期出生質量にサンプリングする場合（[`generate_stars_mass`](@ref) で実装されているように）とは異なり、固定の絶対光度まで集団を生成する場合、現在まで生き残った星のみが集団のフラックスに寄与します。`mag_lim` および `mag_lim_name` キーワード引数を渡して返される星の見かけの光度を制限することを選択した場合、選択した制限よりも暗い星もサンプリングされ、総集団に対してその光度を寄与しますが、返される出力には含まれません。
