```
fmi2SetDebugLogging(c::FMU2Component)
```

ログコールバック関数の使用を制御します。バージョンに依存しません。

# 引数

  * `c::FMU2Component`: 引数 `c` は、FMI 2.0.2 標準における FMU のインスタンス化されたインスタンスを表す可変構造体です。

# 戻り値

  * `status::fmi2Status`: 戻り値 `status` は `fmi2Status` 型の列挙であり、関数呼び出しの成功を示します。

より詳細には：

  * `fmi2OK`: 問題なし
  * `fmi2Warning`: いくつかの問題があるが、計算は続行可能
  * `fmi2Discard`: スレーブが通信ステップのサブインターバルのみを正常に計算した場合
  * `fmi2Error`: 通信ステップを全く実行できなかった場合
  * `fmi2Fatal`: FMU を不可逆的に破損させるエラーが発生した場合
  * `fmi2Pending`: スレーブが非同期に関数を実行する場合にこのステータスが返されます

# 出典

  * FMISpec2.0.2 リンク: [https://fmi-standard.org/](https://fmi-standard.org/)
  * FMISpec2.0.2[p.22]: 2.1.2 プラットフォーム依存の定義 (fmi2TypesPlatform.h)
  * FMISpec2.0.2[p.22]: 2.1.3 関数によって返されるステータス
  * FMISpec2.0.2[p.22]: 2.1.5 FMU インスタンスの作成、破棄、およびログ記録

また、[`fmi2SetDebugLogging`](@ref) も参照してください。
