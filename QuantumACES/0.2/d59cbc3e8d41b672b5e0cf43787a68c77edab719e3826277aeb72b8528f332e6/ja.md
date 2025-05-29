```
RotatedPlanarParameters
```

回転平面コードのシンドローム抽出回路のパラメータ。

# フィールド

  * `params::Dict{Symbol, Any}`: 以下に説明する回路パラメータの辞書。
  * `circuit_name::String`: データ保存に使用される回路の名前。

# パラメータ

  * `vertical_dist::Int`: コードの垂直（Z）距離。
  * `horizontal_dist::Int`: コードの水平（X）距離。
  * `check_type::Symbol`: 回路で使用される安定器のタイプ、`:xzzx` または `:standard` のいずれか。
  * `gate_type::Symbol`: 回路で使用される二量子ゲートのタイプ、`:cx` または `:cz` のいずれか。
  * `dynamically_decouple::Bool`: 回路を動的にデカップリングするかどうか； `true` は現在 `:xzzx` と `:cz` のみサポートされています。
  * `ancilla_measurement::Bool`: 中間回路のアンシラ測定を含めるかどうか。
  * `pad_identity::Bool`: 単一量子アイデンティティゲートでレイヤーをパディングするかどうか。
  * `layer_time_dict::Dict{Symbol, Float64}`: レイヤー時間の辞書。
