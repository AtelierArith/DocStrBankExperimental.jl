```
fmi2GetFMUstate(c::FMU2Component)
```

内部のFMU状態のコピーを作成し、このコピーへのポインタを返します。

# 引数

  * `c::FMU2Component`: FMI 2.0.2標準におけるFMUのインスタンス化されたインスタンスを表す可変構造体。

# 戻り値

  * 戻り値 `state` は内部のFMU状態のコピーへのポインタです。

# 出典

  * FMISpec2.0.2 リンク: [https://fmi-standard.org/](https://fmi-standard.org/)
  * FMISpec2.0.2[p.16]: 2.1.2 プラットフォーム依存の定義 (fmi2TypesPlatform.h)
  * FMISpec2.0.2[p.25]: 2.1.8 完全なFMU状態の取得と設定

他の情報は[`fmi2GetFMUstate`](@ref)を参照してください。
