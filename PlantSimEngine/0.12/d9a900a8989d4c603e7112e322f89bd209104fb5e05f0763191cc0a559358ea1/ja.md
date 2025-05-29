```
TimeStepTable{Status}(df::DataFrame)
```

`DataFrame` から `TimeStepTable` を構築するメソッドですが、各行は `Status` になります。

# 注記

[`ModelList`](@ref) はデフォルトで `TimeStepTable{Status}` を使用します（以下の例を参照）。

# 例

```julia
using PlantSimEngine, DataFrames

# DataFrame からの TimeStepTable:
df = DataFrame(
    Tₗ=[25.0, 26.0],
    aPPFD=[1000.0, 1200.0],
    Cₛ=[400.0, 400.0],
    Dₗ=[1.0, 1.2],
)
TimeStepTable{Status}(df)

# 変数のうち少なくとも1つに複数の値を持つ葉は、自動的に時間ステップを持つ 
# TimeStepTable{Status} を使用します:
models = ModelList(
    process1=Process1Model(1.0),
    process2=Process2Model(),
    process3=Process3Model(),
    status=(var1=15.0, var2=0.3)
)

# 葉のステータスは TimeStepTable です:
status(models)

# もちろん、手動で Status を持つ TimeStepTable を作成することもできます:
TimeStepTable(
    [
        Status(Tₗ=25.0, aPPFD=1000.0, Cₛ=400.0, Dₗ=1.0),
        Status(Tₗ=26.0, aPPFD=1200.0, Cₛ=400.0, Dₗ=1.2),
    ]
)
```
