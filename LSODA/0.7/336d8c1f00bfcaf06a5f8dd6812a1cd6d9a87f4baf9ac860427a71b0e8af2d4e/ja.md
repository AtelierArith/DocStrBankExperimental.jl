lsoda(f::Function, y0::Vector{Float64}, tspan::Vector{Float64}; userdata::Any=nothing, reltol::Union{Float64,Vector}=1e-4, abstol::Union{Float64,Vector}=1e-10)

LSODAアルゴリズムを使用して常微分方程式のセットを解きます。インプレースのf::Functionにエンコードされたベクトル場は、自己説明的な引数f(t, y, ydot, data)を持っている必要があります。
