デフォルトでは、`AbstractInterpreter`は以下の推論バイアウトロジックを実装しています：

  * `bail_out_toplevel_call(::AbstractInterpreter, sig, ::InferenceState)`：トップレベルおよび非具体的な呼び出しサイト`callsig`を推論する際に、手続き間推論からバイアウトします。
  * `bail_out_call(::AbstractInterpreter, rt, ::InferenceState)`：戻り値の型`rt`が`Any`に成長する際に、手続き間推論からバイアウトします。
  * `bail_out_apply(::AbstractInterpreter, rt, ::InferenceState)`：戻り値の型`rt`が`Any`に成長する際に、`_apply_iterate`推論からバイアウトします。

また、任意のラティス要素が`Bottom`に達した場合、ローカルステートメント/フレーム推論からもバイアウトしますが、`AbstractInterpreter`はそれを構成するための特定のインターフェースを提供していません。
