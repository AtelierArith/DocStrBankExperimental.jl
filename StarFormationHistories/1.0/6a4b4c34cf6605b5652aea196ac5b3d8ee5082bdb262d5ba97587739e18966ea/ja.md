```
LogarithmicAMR(α::Real,
               β::Real,
               T_max::Real = 137//10,
               MH_func = MH_from_Z,
               dMH_dZ = dMH_dZ,
               free::NTuple{2, Bool} = (true, true))
```

[`AbstractAMR`](@ref StarFormationHistories.AbstractAMR)のサブタイプで、平均金属質量比 `Z` が、見かけの時間 $t_j$ (Gyr単位) において `Z = α * (T_max - t_j) + β` である対数年齢-金属量関係を実装しています。したがって、`α` はGyrあたりの金属質量比の変化率を表す傾きであり、`β` は `T_max` の見かけの時間において生まれる星の平均金属質量比で、Gyr単位です。`MH_func` は、単一の引数 `Z` を受け取り、[M/H] に変換する呼び出し可能な関数（例：関数）でなければなりません。デフォルトの関数は PARSEC 星モデルに適しています。`dMH_dZ` は、単一の引数 `Z` を受け取り、`MH_func` の `Z` に関する導関数を返す呼び出し可能な関数でなければなりません。`free` は、[`fit_sfh`](@ref) に渡す際に `α` と `β` を自由にフィットさせるか固定するかを制御します。`free[1] == true` の場合、`α` は自由にフィットされ、`free[1] == false` の場合は固定されます。`free[2]` は `β` に対して同じ効果を持ちます。
