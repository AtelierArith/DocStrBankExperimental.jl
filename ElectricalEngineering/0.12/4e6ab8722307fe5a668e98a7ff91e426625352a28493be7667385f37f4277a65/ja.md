# 関数呼び出し

`∠(phi)`

# 説明

長さ1および角度`phi`の複素量を作成します。

# 変数

`phi` 複素量の角度; モジュールUnitfulが利用されている場合、角度は単位`°`を使用して度で指定できます。

# 例

```julia
julia> using Unitful, Unitful.DefaultSymbols, ElectricalEngineering
julia> U1 = 2V*∠(90°)
-0.0 + 2.0im V
```
