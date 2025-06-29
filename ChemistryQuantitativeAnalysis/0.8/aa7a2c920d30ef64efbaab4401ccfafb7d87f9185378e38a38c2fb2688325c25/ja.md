```
MultipleCalibration{A, N, T <: Table} <: AbstractCalibration{A, N}
```

キャリブレーション曲線のためのすべてのデータと設定を保持する可変型。`A`は分析物のタイプを決定し、`N`は数値タイプを決定します。`GLM`の問題のため、`Float64`のみがサポートされています。

# フィールド

  * `analyte`: `Tuple{A, Any}`。最初の要素は定量化される分析物で、2番目の要素は内部標準で、`nothing`は内部標準がないことを示します。
  * `type`: `Bool`は線形線（`true`）または二次曲線（`false`）をフィッティングするかどうかを決定します。
  * `zero`: `Bool`は曲線が(0, 0)を通過するように強制するか（`true`）無視するか（`false`）を決定します。
  * `weight`: `Float64`は、重み付けベクトルとして各要素の`x`に適用される指数を表します。
  * `formula`: `FormulaTerm`、キャリブレーション曲線をフィッティングするための式。
  * `table`: `TypedTable.Table`、クリーンアップされたキャリブレーションデータで、7つの列を含みます。

      * `id`: ポイント名
      * `level`: 濃度レベルのインデックス。大きいほど高い濃度を表します。
      * `y`: 信号または相対信号
      * `x`: 真の濃度
      * `x̂`: 予測濃度
      * `accuracy`: 精度、すなわち`x̂/x`。
      * `include`: このポイントが含まれているかどうか
  * `model`: `GLM`オブジェクト。
