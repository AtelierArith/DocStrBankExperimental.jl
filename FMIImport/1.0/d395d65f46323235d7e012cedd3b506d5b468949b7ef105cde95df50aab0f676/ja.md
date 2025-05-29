```
fmi2FreeFMUstate(c::FMU2Component, state::fmi2FMUstate)
```

FMU状態のために割り当てられたメモリを解放します

# 引数

  * `c::FMU2Component`: FMI 2.0.2標準におけるFMUのインスタンス化されたインスタンスを表す可変構造体。
  * `state::fmi2FMUstate`: 引数`state`は、実際のまたは以前の時間瞬間の内部FMU状態を保存するFMU内のデータ構造へのポインタです。

# 戻り値

  * 戻す値がない場合（Cのvoid関数のように）や、変数またはフィールドが値を持たない場合は、`Nothing`型のシングルトンインスタンスを返します。

# 出典

  * FMISpec2.0.2リンク: [https://fmi-standard.org/](https://fmi-standard.org/)
  * FMISpec2.0.2[p.16]: 2.1.2 プラットフォーム依存の定義 (fmi2TypesPlatform.h)
  * FMISpec2.0.2[p.16]: 2.1.3 関数によって返されるステータス
  * FMISpec2.0.2[p.25]: 2.1.8 完全なFMU状態の取得と設定

```
