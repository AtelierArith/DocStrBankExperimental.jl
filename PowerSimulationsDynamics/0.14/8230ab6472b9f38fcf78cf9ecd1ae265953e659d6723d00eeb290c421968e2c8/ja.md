```
get_real_current_series(
        res::SimulationResults,
        name::String,
)
```

動的注入系列のDAEソリューションから実際の電流時系列を取得する関数。

# 引数

  * `res::SimulationResults` : ソリューションを含むシミュレーション結果オブジェクト
  * `name::String` : 指定されたデバイスを識別するための名前
