```
get_hex_param(vertical_dist::Integer, horizontal_dist::Integer; kwargs...)
get_hex_param(dist::Integer; kwargs...)
```

[`HeavyHexParameters`](@ref) オブジェクトを返し、ヘビーヘックスコードのシンドローム抽出回路をパラメータ化します。

デフォルトのゲートレイヤー時間は、2024年のIBMトリノから推定されています。

# 引数

  * `vertical_dist::Int`: コードの垂直距離。
  * `horizontal_dist::Int`: コードの水平方向の距離。
  * `dist::Int`: コードの距離。これは `vertical_dist = dist` および `horizontal_dist = dist` を設定することと同等です。

# キーワード引数

  * `flipped::Bool = false`: アンシラ量子ビットのレイアウトを左右反転するかどうか。
  * `gate_type::Symbol = :cx`: 回路で使用される二量子ビットゲートのタイプ。
  * `ancilla_measurement::Bool = true`: 中間回路リセットを含めるかどうか。
  * `pad_identity::Bool = true`: 単一量子ビットのアイデンティティゲートでレイヤーをパディングするかどうか。
  * `single_qubit_time::Real = 32`: 単一量子ビットゲートを実装するのにかかる時間（ナノ秒）。
  * `two_qubit_time::Real = 200`: 二量子ビットゲートを実装するのにかかる時間（ナノ秒）。
  * `meas_reset_time::Real = 2500`: 回路の最後で測定とリセットを行うのにかかる時間（ナノ秒）。
  * `meas_reset_time::Real = 2500`: 中間回路リセットを行うのにかかる時間（ナノ秒）。

```
