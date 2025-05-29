```julia
count_equalities(urns::AbstractArray{T<:Integer, 1}) -> Any

```

パーティションによって暗示される等式制約の数をカウントします。これは制約のいくつかの優雅な順序を仮定します。たとえば、パーティション $\{\{\theta_1, \theta_3\}, \{\theta_2\}\}$ は $\theta_1 = \theta_3 \neq \theta_2$ と書くことができ、したがって `count_equalities([1, 2, 1]) == 1` となります。
