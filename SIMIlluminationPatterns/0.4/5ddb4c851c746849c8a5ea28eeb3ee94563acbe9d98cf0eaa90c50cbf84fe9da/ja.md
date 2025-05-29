```
SampledIlluminationPattern{T<:Real,N,IP<:IlluminationPattern{N}}
SampledIlluminationPattern([T=Float64], ip::IlluminationPattern, Δxy)
```

`N`次元のサンプリングされた照明パターン。ピクセルサイズ（`Δxy`）を固定し、センサーと光学系のセットアップでパターンをサンプリングできます。

# 例

```jldoctest;  filter = r"(\d*)\.(\d{4})\d+" => s"\1.\2***"
julia> h = Harmonic(1.0, π / 4, 2 / 61u"nm", 0.0)
Harmonic2D(m=1.0, θ=0.785, ν=0.0328 nm^-1, ϕ=0.0)

julia> sampled_ip = SampledIlluminationPattern(h, (30u"nm", 30u"nm"))
Harmonic2D(m=1.0, θ=0.785, ν=0.0328 nm^-1, ϕ=0.0)(Δxy = 30 nm) with eltype Float64

julia> sampled_ip(3, 4.5)
1.1048934112868387

julia> sampled_ip(CartesianIndex(1,1))
0.6126893879715403

julia> img = rand(10,10);

julia> sampled_ip((5, 5))
5×5 Matrix{Float64}:
 1.5       0.832154  0.612689  1.42788   1.10004
 0.832154  0.612689  1.42788   1.10004   0.504955
 0.612689  1.42788   1.10004   0.504955  1.23233
 1.42788   1.10004   0.504955  1.23233   1.33906
 1.10004   0.504955  1.23233   1.33906   0.54003

julia> sampled_ip((10, 10)) == sampled_ip(img)
true

julia> sampled_ip(CartesianIndices(img)) != sampled_ip(img) # 注意！これは同等ではありません
true

julia> sampled_ip(CartesianIndices((0:9, 0:9))) == sampled_ip(img) # これは同等です
true
```
