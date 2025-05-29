```
get_field_current_series(
        res::SimulationResults,
        name::String,
)
```

動的発電機のDAEソリューションからフィールド電流の時間系列を取得する関数。

# 引数

  * `res::SimulationResults` : ソリューションを含むシミュレーション結果オブジェクト
  * `name::String` : 指定されたデバイスを識別するための名前
