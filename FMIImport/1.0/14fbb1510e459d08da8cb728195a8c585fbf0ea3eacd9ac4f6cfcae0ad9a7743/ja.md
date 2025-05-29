```
fmi2SerializedFMUstateSize(c::FMU2Component, state::fmi2FMUstate)
```

FMUstateを格納できるバイトベクターのサイズを返します。

# 引数

  * `c::FMU2Component`: ミュータブル構造体で、FMI 2.0.2標準におけるFMUのインスタンス化されたインスタンスを表します。
  * `state::fmi2FMUstate`: 引数`state`は、実際のまたは前の時間瞬間の内部FMU状態を保存するFMU内のデータ構造へのポインタです。

# 戻り値

  * 戻り値`size`は、`Csize_t`型の値を安全に参照するオブジェクトです。

# ソース

  * FMISpec2.0.2 リンク: [https://fmi-standard.org/](https://fmi-standard.org/)
  * FMISpec2.0.2[p.16]: 2.1.2 プラットフォーム依存の定義 (fmi2TypesPlatform.h)
  * FMISpec2.0.2[p.16]: 2.1.3 関数によって返されるステータス
  * FMISpec2.0.2[p.25]: 2.1.8 完全なFMU状態の取得と設定

[`fmi2SerializedFMUstateSize`](@ref)も参照してください。
