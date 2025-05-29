```
fmi2GetRealOutputDerivatives(c::FMU2Component, vr::fmi2ValueReferenceFormat, order::AbstractArray{fmi2Integer})
```

実数入力変数の n 番目の時間微分を設定します。

# 引数

  * `c::FMU2Component`: 可変構造体で、FMI 2.0.2 標準における FMU のインスタンスを表します。
  * `vr::Array{fmi2ValueReference}`: 引数 `vr` は、微分を設定する変数を定義する「ValueReference」と呼ばれる `nvr` 値ハンドルの配列です。
  * `order::Array{fmi2Integer}`: 引数 `order` は、実数入力変数の対応する微分の順序を指定する fmi2Integer 値の配列です。

# 戻り値

  * `value::AbstactArray{fmi2Integer}`: 戻り値 `value` は、微分の値を持つベクトルを表す配列です。

# 出典

  * FMISpec2.0.2 リンク: [https://fmi-standard.org/](https://fmi-standard.org/)
  * FMISpec2.0.2[p.16]: 2.1.2 プラットフォーム依存の定義
  * FMISpec2.0.2[p.18]: 2.1.3 関数によって返されるステータス
  * FMISpec2.0.2[p.104]: 4.2.1 入力/出力値およびパラメータの転送
