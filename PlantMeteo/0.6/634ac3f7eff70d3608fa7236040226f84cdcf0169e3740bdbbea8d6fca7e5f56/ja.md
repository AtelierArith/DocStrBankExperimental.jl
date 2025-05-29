```
TimeStepTable(vars)
```

`TimeStepTable`は、各時間ステップの変数値を保存します。*例*として、気象変数があります。これは`Tables.jl`インターフェースを実装しているため、`Tables.jl`を使用する任意のパッケージ（`DataFrames.jl`など）で使用できます。

独自の変数を保存するために`TimeStepTable`を拡張するには、変数の保存のための新しい型を定義します。実装の例として、[`Atmosphere`](@ref)型を参照するか、[`PlantSimEngine.jl`](https://github.com/VEZY/PlantSimEngine.jl)の`Status`型を確認できます。

# 例

```julia
data = TimeStepTable(
    [
        Atmosphere(T = 20.0, Wind = 1.0, P = 101.3, Rh = 0.65),
        Atmosphere(T = 23.0, Wind = 1.5, P = 101.3, Rh = 0.60),
        Atmosphere(T = 25.0, Wind = 3.0, P = 101.3, Rh = 0.55)
    ]
)

# DataFrameに変換できます：
using DataFrames
df = DataFrame(data)

# DataFrameからTimeStepTableを作成することもできます：
TimeStepTable(df)

# デフォルトでは、変数を高性能で保存するためにNamedTupleを使用します。
# もし異なる型を使用したい場合は、型パラメータとして指定できます（*例*として可変性や事前計算など）：
TimeStepTable{Atmosphere}(df)
# またはPlantSimEngineを使用する場合：TimeStepTable{Status}(df)
```
