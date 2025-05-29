```
fmi2SetFMUstate(c::FMU2Component, FMUstate::fmi2FMUstate)
```

以前にコピーされたFMUstateの内容を戻し、それを実際の新しいFMU状態として使用します。

# 引数

  * `str::fmi2Struct`: FMI 2.0.2標準におけるFMUの代表。

詳細: `fmi2Struct = Union{FMU2, FMU2Component}`

  * `str::FMU2`: FMI 2.0.2標準におけるFMUおよびそのすべてのインスタンスを表す可変構造体。
  * `str::FMU2Component`: FMI 2.0.2標準におけるFMUのインスタンス化されたインスタンスを表す可変構造体。
  * `FMUstate::fmi2FMUstate`: 引数`FMUstate`は、実際のまたは以前の時間瞬間の内部FMU状態を保存するFMU内のデータ構造へのポインタです。

# 戻り値

  * `status::fmi2Status`: 戻り値`status`は`fmi2Status`型の列挙であり、関数呼び出しの成功を示します。

詳細:

  * `fmi2OK`: すべて正常
  * `fmi2Warning`: 物事は完全に正しくはないが、計算は続行できる
  * `fmi2Discard`: スレーブが通信ステップのサブインターバルのみを正常に計算した場合
  * `fmi2Error`: 通信ステップを全く実行できなかった場合
  * `fmi2Fatal`: FMUを不可逆的に破損させるエラーが発生した場合
  * `fmi2Pending`: スレーブが関数を非同期に実行する場合にこのステータスが返される

# 出典

  * FMISpec2.0.2 リンク: [https://fmi-standard.org/](https://fmi-standard.org/)
  * FMISpec2.0.2[p.16]: 2.1.2 プラットフォーム依存の定義 (fmi2TypesPlatform.h)
  * FMISpec2.0.2[p.16]: 2.1.3 関数によって返されるステータス
  * FMISpec2.0.2[p.25]: 2.1.8 完全なFMU状態の取得と設定

また[`fmi2GetFMUstate`](@ref)も参照してください。
