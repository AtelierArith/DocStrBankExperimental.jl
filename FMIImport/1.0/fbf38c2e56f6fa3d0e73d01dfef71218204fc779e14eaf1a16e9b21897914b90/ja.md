```
fmi3GetFMUState(c::FMU3Instance)
```

内部のFMU状態のコピーを作成し、このコピーへのポインタを返します。

# 引数

  * `c::FMU3Instance`: FMI 3.0標準におけるFMUのインスタンス化されたインスタンスを表す可変構造体。

# 戻り値

  * 戻り値 `state` は内部のFMU状態のコピーへのポインタです。

# ソース

  * FMISpec3.0 リンク: [https://fmi-standard.org/](https://fmi-standard.org/)
  * FMISpec3.0: 2.2.3 プラットフォーム依存の定義
  * FMISpec3.0: 2.2.6.4. 完全なFMU状態の取得と設定

他にも [`fmi3GetFMUState`](@ref) を参照してください。
