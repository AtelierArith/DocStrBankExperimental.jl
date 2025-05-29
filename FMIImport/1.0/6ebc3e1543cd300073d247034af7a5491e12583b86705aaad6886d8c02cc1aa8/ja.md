```
fmi3SerializedFMUStateSize(c::FMU3Instance, state::fmi3FMUState)
```

FMUstateを格納できるバイトベクターのサイズを返します。

# 引数

  * `c::FMU3Instance`: 可変構造体で、FMI 3.0標準におけるFMUのインスタンス化されたインスタンスを表します。
  * `state::fmi3FMUState`: 引数`state`は、実際のまたは以前の時間瞬間の内部FMU状態を保存するFMU内のデータ構造へのポインタです。

# 戻り値

  * 戻り値`size`は、`Csize_t`型の値を安全に参照するオブジェクトです。

# ソース

  * FMISpec3.0リンク: [https://fmi-standard.org/](https://fmi-standard.org/)
  * FMISpec3.0: 2.2.3 プラットフォーム依存定義
  * FMISpec3.0: 2.2.6.4. 完全なFMU状態の取得と設定

[`fmi3SerializedFMUStateSize`](@ref)も参照してください。
