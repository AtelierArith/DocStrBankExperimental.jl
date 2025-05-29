`SurfaceVelocityData`をRabatel et. al (2023)のデータを使用して、与えられたパラメータ（デフォルトのものを含む）で構築します。

```julia
function SurfaceVelocityData(;     
    x::Union{Vector{F}, Nothing} = nothing,     
    y::Union{Vector{F}, Nothing} = nothing,     
    lat::Union{Vector{F}, Nothing} = nothing,     
    lon::Union{Vector{F}, Nothing} = nothing,     
    vx::Union{Vector{Matrix{F}}, Nothing} = nothing,     
    vy::Union{Vector{Matrix{F}}, Nothing} = nothing,     
    vabs::Union{Vector{Matrix{F}}, Nothing} = nothing,     
    vx*error::Union{Vector{F}, Nothing} = nothing,     
    vy*error::Union{Vector{F}, Nothing} = nothing,     
    vabs*error::Union{Vector{F}, Nothing} = nothing,     
    date::Union{Vector{DateTime}, Nothing} = nothing,     
    date1::Union{Vector{DateTime}, Nothing} = nothing,     
    date2::Union{Vector{DateTime}, Nothing} = nothing,     
    date*error::Union{Vector{Day}, Vector{Millisecond}, Nothing} = nothing,     
    isGridGlacierAligned::Bool = false, 
) where {F <: AbstractFloat}
```

Rabatel et. al (2023)に基づく氷表面速度データのコンストラクタです。

重要な注意事項：

  * 速度の誤差は、ピクセル分布ではなく、タイムスタンプごとにユニークです。
  * 絶対速度の誤差 `vabs_error` は過大評価されています。

参考文献：     

  * Rabatel, A., Ducasse, E., Millan, R. & Mouginot, J.

Satellite-Derived Annual Glacier Surface Flow Velocity Products for the European Alps,        2015–2021.        Data 8, 66 (2023).
