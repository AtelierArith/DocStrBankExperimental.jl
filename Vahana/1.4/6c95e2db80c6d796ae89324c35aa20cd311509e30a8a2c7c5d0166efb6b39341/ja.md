```
calc_raster(sim, raster::Symbol, f, f_returns::DataType, accessible::Vector{DataType})
```

`raster`の値を計算するために、`add_raster!`関数によって構築された各セルIDに`f`を適用します。

`f_returns`は関数fが返す型でなければなりません。この型にはゼロ関数の実装が必要であり、zero(returntype) | f(id)はf(id)と等しくなければなりません。

`accessible`はエージェントおよび/またはエッジ型のベクターです。このベクターは、直接（例：[`agentstate`](@ref)を介して）または間接的に（例：[`neighborstates`](@ref)を介して）アクセスされるすべての型をリストする必要があります。

`calc_raster`の結果がセルの状態のみに依存し（以下の例のように）、すべてのセルが同じ型である場合、[`calc_rasterstate`](@ref)を簡潔な代替手段として使用できます。

`raster`と同じ次元を持つn次元配列をその値で返します。

例：

以下のコードは「ライフゲーム」の実装からのもので、どのセルが生きているかを示すブール行列を生成します（したがって、内部グラフ構造を細胞オートマトンの通常の表現にマッピングします）：

```@example
    calc_raster(sim, :raster, id -> agentstate(sim, id, Cell).active, Bool, [ Cell ]) 
```

[`finish_init!`](@ref)の後にのみ呼び出すことができます。

他に[`add_raster!`](@ref)および[`calc_rasterstate`](@ref)も参照してください。
