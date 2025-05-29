```
LinearAMR(α::Real,
          β::Real,
          T_max::Real = 137//10,
          free::NTuple{2, Bool} = (true, true))
```

[`AbstractAMR`](@ref StarFormationHistories.AbstractAMR) のサブタイプで、平均金属量が見かけの時間 $t_j$ (Gyr単位) において `μ_j = α * (T_max - t_j) + β` である線形年齢-金属量関係を実装しています。したがって、`α` はGyrあたりの金属量の変化率を表す傾きであり、`β` は `T_max` の見かけの時間において生まれる星の平均金属量の値で、単位はGyrです。`free` は、[`fit_sfh`](@ref) に渡されたときに `α` と `β` を自由にフィットさせるか固定するかを制御します。`free[1] == true` の場合、`α` は自由にフィットされ、`free[1] == false` の場合は固定されます。`free[2]` は `β` に対して同じ効果を持ちます。
