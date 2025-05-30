```
get_chp_defaults_prime_mover_size_class(;hot_water_or_steam::Union{String, Nothing}=nothing,
                                    avg_boiler_fuel_load_mmbtu_per_hour::Union{Float64, Vector{Float64}, Nothing}=nothing,
                                    prime_mover::Union{String, Nothing}=nothing,
                                    size_class::Union{Int64, Nothing}=nothing,
                                    max_kw::Float64=NaN,
                                    boiler_efficiency::Union{Float64, Nothing}=nothing,
                                    avg_electric_load_kw::Union{Float64, Nothing}=nothing,
                                    max_electric_load_kw::Union{Float64, Nothing}=nothing,
                                    is_electric_only::Bool=false,
                                    thermal_efficiency::Float64=NaN)
```

入力のセットに応じて、すべてのCHPコストおよび性能パラメータのデフォルトに加えて、異なる出力セットが決定されます:     1. 入力: hot*water*or*steam と avg*boiler*fuel*load*mmbtu*per*hour        出力: prime*mover, size*class, chp*elec*size*heuristic*kw, chp*max*size*kw     2. 入力: prime*mover と avg*boiler*fuel*load*mmbtu*per*hour        出力: size*class, chp*elec*size*heuristic*kw, chp*max*size*kw     3. 入力: prime*mover と size*class        出力: (デフォルトの hot*water*or*steam を使用), chp*max*size*kw     4. 入力: prime*mover        出力: デフォルトの平均 size*class = 0, chp*max*size*kw     5. 入力: prime*mover, avg*electric*load*kw, max*electric*load*kw        出力: chp*elec*size*heuristic*kw, chp*max*size*kw

この関数の主な目的は、CHPデフォルトの依存関係のマッピングを以下のように伝えることです:      hot*water*or*steam と avg*boiler*fuel*load*mmbtu*per*hour: hot*water かつ <= 27 MMBtu/hr avg*boiler*fuel*load*mmbtu*per*hour –> prime*mover = recip*engine of size*class X hot*water かつ > 27 MMBtu/hr avg*boiler*fuel*load*mmbtu*per*hour –> prime*mover = combustion*turbine of size*class X steam かつ <= 7 MMBtu/hr avg*boiler*fuel*load*mmbtu*per*hour –> prime*mover = recip*engine of size*class X steam かつ > 7 MMBtu/hr avg*boiler*fuel*load*mmbtu*per*hour –> prime*mover = combustion*turbine of size_class X

閾値 avg*boiler*fuel*load*mmbtu*per*hour は、産業の専門家の判断に基づいており、往復動エンジンは小型サイズと温水により適しており、燃焼タービンは大型サイズと蒸気により適しています。

サイズクラスとデフォルトの決定は、電力負荷メトリックのみに基づいており、加熱を行わない「CHP」、すなわちプライムジェネレーターのためのものです。 ```
