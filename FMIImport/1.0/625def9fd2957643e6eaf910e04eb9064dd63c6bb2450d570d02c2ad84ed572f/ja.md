```
fmi2SetDebugLogging(c::FMU2Component, loggingOn::fmi2Boolean, nCategories::Unsigned, categories::Ptr{Nothing})
```

ロギングコールバック関数の使用を制御します。バージョンに依存しません。

# 引数

  * `c::FMU2Component`: 引数 `c` は、FMI 2.0.2 標準におけるインスタンス化された FMU のインスタンスを表す可変構造体です。
  * `loggingOn::fmi2Boolean`: `loggingOn = fmi2True` の場合、categories で指定されたログカテゴリのデバッグロギングが有効になります。それ以外の場合は無効になります。型 `fmi2Boolean` は C 型のブール値のエイリアスタイプとして定義されており、`fmi2True` および `fmi2False` と共に使用されます。
  * `nCategories::Unsigned`: 引数 `nCategories` は、引数 `categories` の長さを定義します。
  * `categories::Ptr{Nothing}`:

# 戻り値

  * `status::fmi2Status`: 戻り値 `status` は `fmi2Status` 型の列挙体で、関数呼び出しの成功を示します。

より詳細には：

  * `fmi2OK`: 問題なし
  * `fmi2Warning`: いくつかの問題がありますが、計算は続行できます
  * `fmi2Discard`: スレーブが通信ステップのサブインターバルのみを正常に計算した場合
  * `fmi2Error`: 通信ステップを全く実行できなかった場合
  * `fmi2Fatal`: FMU を不可逆的に破損させるエラーが発生した場合
  * `fmi2Pending`: スレーブが関数を非同期に実行する場合にこのステータスが返されます

# 出典

  * FMISpec2.0.2 リンク: [https://fmi-standard.org/](https://fmi-standard.org/)
  * FMISpec2.0.2[p.22]: 2.1.2 プラットフォーム依存の定義 (fmi2TypesPlatform.h)
  * FMISpec2.0.2[p.22]: 2.1.3 関数によって返されるステータス
  * FMISpec2.0.2[p.22]: 2.1.5 FMU インスタンスの作成、破壊、およびロギング

[`fmi2SetDebugLogging`](@ref) も参照してください。
