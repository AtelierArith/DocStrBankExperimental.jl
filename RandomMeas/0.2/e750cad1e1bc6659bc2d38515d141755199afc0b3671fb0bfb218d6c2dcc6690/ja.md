```
get_fidelity(
    group_1::MeasurementGroup,
    group_2::MeasurementGroup,
    subsystem::Vector{Int} = collect(1:group_1.N)
)
```

2つの量子状態の忠実度を計算します Tr(ρ1 ρ2)/SROOT(Tr(ρ1^2),Tr(ρ2^2)) 測定データから測定結果の重なりを平均することによって。

# 引数

  * `group_1::MeasurementGroup`: 最初の状態の測定データ。
  * `group_2::MeasurementGroup`: 2番目の状態の測定データ。
  * `subsystem::Vector{Int}` (オプション): 保持するサブシステムを指定するサイトインデックスのベクトル。デフォルトは全システム。

# 戻り値

  * 計算された忠実度。
