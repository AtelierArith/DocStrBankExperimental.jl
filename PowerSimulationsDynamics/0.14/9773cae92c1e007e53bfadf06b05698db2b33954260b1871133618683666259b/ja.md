```
get_activepower_series(
        res::SimulationResults,
        name::String,
)
```

動的注入系列のDAEソリューションからアクティブパワー出力の時間系列を取得する関数です。

# 引数

  * `res::SimulationResults` : ソリューションを含むシミュレーション結果オブジェクト
  * `name::String` : 指定されたデバイスを識別するための名前
