```
fmi3SetDebugLogging(c::FMU3Instance, logginOn::fmi3Boolean, nCategories::UInt, categories::Ptr{Nothing})
```

ロギングコールバック関数の使用を制御します。バージョンに依存しません。

# 引数

  * `c::FMU3Instance`: 引数 `c` は、FMI 3.0 標準における FMU のインスタンス化されたインスタンスを表す可変構造体です。
  * `logginOn::fmi3Boolean`: `loggingOn = fmi3True` の場合、categories で指定されたログカテゴリのデバッグロギングが有効になります。それ以外の場合は無効になります。`fmi3Boolean` 型は C 型のブール値のエイリアスタイプとして定義されており、`fmi3True` および `fmi3False` と共に使用されます。
  * `nCategories::UInt`: 引数 `nCategories` は、引数 `categories` の長さを定義します。
  * `categories::Ptr{Nothing}`:

# 戻り値

  * `status::fmi3Status`: 戻り値 `status` は `fmi3Status` 型の列挙であり、関数呼び出しの成功を示します。

詳細は以下の通りです：

  * `fmi3OK`: 問題なし
  * `fmi3Warning`: いくつかの問題がありますが、計算は続行できます
  * `fmi3Discard`: スレーブが通信ステップのサブインターバルのみを正常に計算した場合
  * `fmi3Error`: 通信ステップを全く実行できなかった場合
  * `fmi3Fatal`: FMU を不可逆的に破損させるエラーが発生した場合

# ソース

  * FMISpec3.0 リンク: [https://fmi-standard.org/](https://fmi-standard.org/)
  * FMISpec3.0: 2.2.3 プラットフォーム依存の定義
  * FMISpec3.0: 2.2.4 関数によって返されるステータス
  * FMISpec3.0: 2.3.1. スーパー状態: FMU 状態の設定可能性

また、[`fmi3SetDebugLogging`](@ref) も参照してください。
