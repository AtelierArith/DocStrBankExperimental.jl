```
get_pss_output_series(
        res::SimulationResults,
        name::String,
)
```

動的発電機のDAEソリューションからpss出力時系列を取得する関数。

# 引数

  * `res::SimulationResults` : ソリューションを含むシミュレーション結果オブジェクト
  * `name::String` : 指定されたデバイスを識別するための名前
