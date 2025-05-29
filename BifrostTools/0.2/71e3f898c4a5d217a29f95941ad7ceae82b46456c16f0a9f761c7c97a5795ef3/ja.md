```
function get_electron_density(
    xp::BifrostExperiment,
    snap::Integer,
    kwargs...)
```

スナップショット `snap` から電子密度を計算する関数です。スライスをサポートしています。ガス密度 `rho` と内部エネルギー `e` はオプションの引数であり、渡すことができます（ただし、cgs単位でなければなりません）。これらの量がすでに存在する場合、それらを渡すことで電子密度の計算が速くなります。

`kwargs`:     units::String="si",     slicex::AbstractVector{<:Integer}=Int[],     slicey::AbstractVector{<:Integer}=Int[],     slicez::AbstractVector{<:Integer}=Int[],     rho::Array{AbstractFloat,3}=Float32[;;;],     e::Array{AbstractFloat,3}=Float32[;;;],     tabfile::String="tabparam.in"
