```
fmi2EnterEventMode(c::FMU2Component; soft::Bool=false)
```

モデルは連続時間モードからイベントモードに入ります。離散時間方程式がアクティブになる可能性があり（関係は「凍結」されません）。

# 引数

  * `c::FMU2Component`: FMI 2.0.2標準でインスタンス化されたFMUのインスタンスを表す可変構造体。

# キーワード

  * `soft::Bool=false`: キーワード `soft = true` の場合、このコマンドはFMUがこのコマンドに対して許可された状態にある場合にのみ実行されます。

# 戻り値

  * `status::fmi2Status`: 戻り値 `status` は `fmi2Status` 型の列挙で、関数呼び出しの成功を示します。

より詳細には：

  * `fmi2OK`: すべて正常
  * `fmi2Warning`: いくつかの問題がありますが、計算は続行できます
  * `fmi2Discard`: スレーブが通信ステップのサブインターバルのみを正常に計算した場合
  * `fmi2Error`: 通信ステップを全く実行できなかった場合
  * `fmi2Fatal`: FMUを不可逆的に破損させるエラーが発生した場合
  * `fmi2Pending`: スレーブが関数を非同期に実行する場合にこのステータスが返されます

# ソース

  * FMISpec2.0.2 リンク: [https://fmi-standard.org/](https://fmi-standard.org/)
  * FMISpec2.0.2[p.16]: 2.1.2 プラットフォーム依存の定義 (fmi2TypesPlatform.h)
  * FMISpec2.0.2[p.16]: 2.1.3 関数によって返されるステータス
  * FMISpec2.0.2[p.83]: 3.2.2 モデル方程式の評価

[`fmi2EnterEventMode`](@ref) も参照してください。
