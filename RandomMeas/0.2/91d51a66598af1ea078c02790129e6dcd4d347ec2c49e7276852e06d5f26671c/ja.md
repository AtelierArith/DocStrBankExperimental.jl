```
export_MeasurementGroup(group::MeasurementGroup{T}, filepath::String)
```

MeasurementGroupオブジェクトをNPZファイルにエクスポートします。

# 引数

  * `group::MeasurementGroup{T}`: 各MeasurementDataがタイプTの独自の測定設定を持つ可能性があるMeasurementGroupオブジェクト（T <: Union{Nothing, LocalUnitaryMeasurementSetting, ComputationalBasisMeasurementSetting}）。
  * `filepath::String`: NPZファイルが書き込まれるファイルパス。

# 詳細

  * 各MeasurementDataオブジェクトからの測定結果（形状(NM, N)の各々）は、形状(NU, NM, N)の3D配列にスタックされます。ここで、NUはMeasurementDataオブジェクトの数です。
  * 測定設定は、存在する場合、サイズNU x N x 2 x 2のComplex配列としてエクスポートされます。
