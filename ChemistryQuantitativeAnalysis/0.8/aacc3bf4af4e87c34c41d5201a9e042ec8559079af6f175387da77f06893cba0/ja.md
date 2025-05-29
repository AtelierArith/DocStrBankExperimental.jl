```
calibration(anisd::Tuple, tbl::Table; analyte = 1, isd = 0, type = true, zero = false, weight = 0)
calibration(batch::Batch{A}, ana::B; id = sample(batch.method.signaltable), isd = isdof(batch.method, analyte),
                    type = true, zero = false, weight = 0) where {A, B <: A}
calibration(method::AnalysisMethod{A}, ana::B; id = sample(method.signaltable), isd = isdof(method, analyte),
            type = true, zero = false, weight = 0) where {A, B <: A}
```

`MultipleCalibration`を作成します。

  * `anisd`: `Tuple{B <: A, Any}`で、`analyte`として保存されます。最初の要素は定量化される分析物で、2番目の要素は内部標準で、`nothing`は内部標準がないことを意味します。
  * `analyte`: `B`で、`analyte`の最初の引数として保存されます。
  * `tbl`: `TypedTable.Table`で、`table`として保存されます。ポイント選択のためのキャリブレーションデータをクリーンアップします。
  * `method`: `AnalysisMethod`、キャリブレーションメソッドとデータ。
  * `batch`: `Batch`。

# キーワード引数

  * `type`: `Bool`で、線形線をフィッティングするか（`true`）二次曲線をフィッティングするか（`false`）を決定し、`type`として保存されます。
  * `zero`: `Bool`で、曲線が（0, 0）を通過するように強制するか（`true`）無視するか（`false`）を決定し、`zero`として保存されます。
  * `weight`: `Float64`で、重み付けベクトルとして各要素の`x`に適用される指数を表し、`weight`として保存されます。
