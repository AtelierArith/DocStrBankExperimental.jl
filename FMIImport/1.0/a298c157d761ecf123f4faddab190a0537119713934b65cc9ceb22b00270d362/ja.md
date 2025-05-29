```
fmi2GetDerivatives(c::FMU2Component)
```

現在の時間瞬間と現在の状態における状態の導関数を計算します。

# 引数

  * `c::FMU2Component`: FMI 2.0.2標準におけるFMUのインスタンスを表す可変構造体。

# 戻り値

  * `derivatives::Array{fmi2Real}`: 現在の状態に対する`derivatives`を表す`fmi2Real`値の配列を返します。導関数ベクトルの要素の順序は状態ベクトルの順序と同じです。

# 出典

  * FMISpec2.0.2 リンク: [https://fmi-standard.org/](https://fmi-standard.org/)
  * FMISpec2.0.2[p.16]: 2.1.2 プラットフォーム依存の定義 (fmi2TypesPlatform.h)
  * FMISpec2.0.2[p.16]: 2.1.3 関数によって返されるステータス
  * FMISpec2.0.2[p.83]: 3.2.2 モデル方程式の評価

他にも[`fmi2GetDerivatives!`](@ref)を参照してください。
