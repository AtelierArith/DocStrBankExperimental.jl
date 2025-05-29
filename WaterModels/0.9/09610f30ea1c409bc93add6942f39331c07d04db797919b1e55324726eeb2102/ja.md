```
constraint_tank_volume_fixed(
    wm::AbstractWaterModel,
    n::Int,
    i::Int,
    V_0::Float64,
    time_step::Float64,
    min_vol::Float64,
    max_vol::Float64
)
```

タンクのある時間インデックスでの体積が固定されることを保証する制約を追加します。ここで、`wm`はWaterModelsオブジェクト、`n`はマルチネットワーク内のサブネットワークのインデックス、`i`はタンクのインデックス、`V_0`は望ましいタンクの固定体積です。また、体積を時間的に前方に統合した後、新しい体積が事前に定義された下限と上限の間に収まることを保証する制約も追加します。そのために、`time_step`は現在の時間インデックスと次の間の時間ステップ、`min_vol`はタンクに存在しなければならない水の最小体積、`max_vol`はタンク内の水の最大体積です。
