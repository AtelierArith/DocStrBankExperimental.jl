```
get_unrotated_param(vertical_dist::Integer, horizontal_dist::Integer; kwargs...)
get_unrotated_param(dist::Integer; kwargs...)
```

未回転平面コードの症候群抽出回路をパラメータ化する[`UnrotatedPlanarParameters`](@ref)オブジェクトを返します。

デフォルトのゲート層時間は、Google Quantum AIによる`Suppressing quantum errors by scaling a surface code logical qubit`（2023）から推定されています。

# 引数

  * `vertical_dist::Int`: コードの垂直（Z）距離。
  * `horizontal_dist::Int`: コードの水平（X）距離。
  * `dist::Int`: コードの距離。この値は`vertical_dist = dist`および`horizontal_dist = dist`を設定することと同等です。

# キーワード引数

  * `gate_type::Symbol = :cx`: 回路で使用される二量子ビットゲートのタイプで、`:cx`でなければなりません。
  * `ancilla_measurement::Bool = true`: 中間回路リセットを含めるかどうか。
  * `pad_identity::Bool = true`: 単一量子ビットのアイデンティティゲートで層をパディングするかどうか。
  * `single_qubit_time::Real = 29`: 単一量子ビットゲートを実装するのにかかる時間（ナノ秒）。
  * `two_qubit_time::Real = 29`: 二量子ビットゲートを実装するのにかかる時間（ナノ秒）。
  * `meas_reset_time::Real = 660`: 回路の最後で測定とリセットを行うのにかかる時間（ナノ秒）。
  * `mid_reset_time::Real = 660`: 中間回路リセットを行うのにかかる時間（ナノ秒）。

```
