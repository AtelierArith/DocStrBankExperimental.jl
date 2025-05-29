```
get_reactivepower_series(
        res::SimulationResults,
        name::String,
)
```

動的インジェクション系列のDAEソリューションからリアクティブパワー出力の時間系列を取得する関数です。

# 引数

  * `res::SimulationResults` : ソリューションを含むシミュレーション結果オブジェクト
  * `name::String` : 指定されたデバイスを識別するための名前
