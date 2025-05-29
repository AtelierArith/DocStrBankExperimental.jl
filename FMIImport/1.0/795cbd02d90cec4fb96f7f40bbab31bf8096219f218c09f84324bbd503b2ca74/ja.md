fmi3GetOutputDerivatives!(c::FMU3Instance, vr::AbstractArray{fmi3ValueReference}, nValueReferences::Csize*t, order::AbstractArray{fmi3Int32}, values::AbstractArray{fmi3Float64}, nValues::Csize*t)

出力値の n 番目の導関数を取得します。

# 引数

  * `c::FMU3Instance`: 可変構造体で、FMI 3.0 標準における FMU のインスタンス化されたインスタンスを表します。
  * `vr::Array{fmi3ValueReference}`: 引数 `vr` は、導関数を設定する変数を定義する "ValueReference" と呼ばれる `nValueReferences` の値ハンドルの配列です。
  * `order::Array{fmi3Int32}`: 引数 `order` は、実入力変数の対応する導関数の順序を指定する fmi3Int32 値の配列です。

# 戻り値

  * `value::AbstactArray{fmi3Float64}`: 戻り値 `value` は、導関数の値を持つベクトルを表す配列です。

# 出典

  * FMISpec3.0 リンク: [https://fmi-standard.org/](https://fmi-standard.org/)
  * FMISpec3.0: 2.2.3 プラットフォーム依存の定義
  * FMISpec3.0: 2.2.12. 連続出力の導関数を取得する

また、[`fmi3GetOutputDerivatives`](@ref)も参照してください。
