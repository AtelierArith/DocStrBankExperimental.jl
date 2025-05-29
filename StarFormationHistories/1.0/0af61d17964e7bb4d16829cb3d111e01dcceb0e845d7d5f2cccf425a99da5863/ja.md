```
calculate_coeffs(MH_model::AbstractMetallicityModel,
                 disp_model::AbstractDispersionModel,
                 mstars::AbstractVector{<:Number}, 
                 logAge::AbstractVector{<:Number},
                 metallicities::AbstractVector{<:Number})
```

指定された金属量モデル `MH_model` と金属量分散モデル `disp_model` を使用して、対数年齢 `logAge` と金属量 `metallicities` のセットを持つ各SSPの星形成質量係数 ($r_{j,k}$ は [導出](@ref mzr_derivation) にあります) を返します。

# 例

```jldoctest; setup = :(import StarFormationHistories: calculate_coeffs, PowerLawMZR, GaussianDispersion)
julia> n_logage, n_mh = 10, 20; # ユニークなlogAgesの数、MHsの数

julia> coeffs = calculate_coeffs(PowerLawMZR(1.0, -1.0),
                                 GaussianDispersion(0.2),
                                 rand(n_logage),
                                 repeat(range(7.0, 10.0; length=n_logage); inner=n_mh),
                                 repeat(range(-2.0, 0.0; length=n_mh); outer=n_logage));

julia> coeffs isa Vector{Float64}
true

julia> length(coeffs) == n_logage * n_mh
true
```
