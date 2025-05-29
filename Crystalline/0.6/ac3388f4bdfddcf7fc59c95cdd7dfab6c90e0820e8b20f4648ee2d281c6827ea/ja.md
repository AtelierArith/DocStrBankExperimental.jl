```
modulate(flat::UnityFourierLattice{D},
modulation::AbstractVector{ComplexF64}=rand(ComplexF64, length(getcoefs(flat))),
expon::Union{Nothing, Real}=nothing, Gs::Union{ReciprocalBasis{D}, Nothing}=nothing)
                        --> ModulatedFourierLattice{D}
```

`UnityFourierLattice` `flat` から具体的な変調フーリエ格子を導出します（*軌道係数*間の*相互関係*を含む）。これは、"正規化された" 軌道係数に `modulation`、すなわち *複素* 変調ベクトルを掛けることによって行われます（一般的には複素であるべきです。そうでない場合、格子に意図しない対称性を復元します）。異なる `modulation` ベクトルは、元の `flat` によって記述される同じ格子の異なる実現を生成します。デフォルトでは、ランダムな複素ベクトルが使用されます。

指数 `expon` を提供することができ、これは短波長の特徴（すなわち高-|G| 軌道）にペナルティ項を導入します。これは、軌道係数を |G|^`expon` で割ることによって行われ、`expon > 0` の場合に "より単純" で "滑らかな" 格子境界を生成します（`expon < 0` の場合はその逆）。これは基本的に格子に対する連続的な "簡素化" 操作に相当します（必ずしも滑らかにする操作ではありません；単に "高周波" 成分を抑制します）。`expon = nothing` の場合、再スケーリングは行われません。`Gs` が `nothing` として提供される場合、軌道ノルムは逆格子基底で計算されます（したがって、格子基底が直交でない場合、厳密にはノルムではないかもしれません）；基底を明示的に考慮するためには、`Gs` を [`ReciprocalBasis`](@ref) として提供する必要があります。詳細は [`normscale`](@ref) を参照してください。
