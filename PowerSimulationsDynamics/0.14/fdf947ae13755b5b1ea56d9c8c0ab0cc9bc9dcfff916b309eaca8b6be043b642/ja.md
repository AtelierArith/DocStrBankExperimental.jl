```
get_field_voltage_series(
        res::SimulationResults,
        name::String,
)
```

動的発電機のDAEソリューションからフィールド電圧の時間系列を取得する関数です。

# 引数

  * `res::SimulationResults` : ソリューションを含むシミュレーション結果オブジェクト
  * `name::String` : 指定されたデバイスを識別するための名前
