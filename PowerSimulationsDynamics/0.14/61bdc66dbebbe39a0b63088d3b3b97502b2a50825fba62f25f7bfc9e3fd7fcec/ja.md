```
get_reactivepower_branch_flow(
        res::SimulationResults,
        name::String,
        location::Symbol,
)
```

ブランチの系列要素を通る無効電力を取得するための関数。ユーザーは、電力が:fromまたは:toバスで計算されるべきかを指定する必要があります。

:fromが指定された場合、電力は:fromバスから外向きに流れるように計算されます。:toが指定された場合、電力は:toバスに流れ込むように計算されます。

# 引数

  * `res::SimulationResults` : 解を含むシミュレーション結果オブジェクト
  * `name::String` : 指定されたラインを識別するための名前
  * `location::Symbol` : バスを指定するための:fromまたは:to
