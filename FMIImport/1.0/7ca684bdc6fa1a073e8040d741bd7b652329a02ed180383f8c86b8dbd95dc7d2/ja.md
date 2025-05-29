```
fmi2EnterContinuousTimeMode(c::FMU2Component; soft::Bool=false)
```

モデルは連続時間モードに入り、すべての離散時間方程式は非アクティブになり、すべての関係は「凍結」されます。この関数は、イベントモードから連続時間モードに変更する際に呼び出す必要があります（すべての関与するFMUおよび他のモデルにおけるイベントモードでのグローバルイベント反復が収束した後）。

# 引数

  * `c::FMU2Component`: FMI 2.0.2標準におけるFMUのインスタンスを表す可変構造体。

# キーワード

  * `soft::Bool=false`: キーワード `soft = true` の場合、このコマンドはFMUがこのコマンドに対して許可された状態にある場合にのみ実行されます。

# 戻り値

  * `status::fmi2Status`: 戻り値 `status` は `fmi2Status` 型の列挙体で、関数呼び出しの成功を示します。

より詳細には：

  * `fmi2OK`: すべて正常
  * `fmi2Warning`: いくつかの問題があるが、計算は続行可能
  * `fmi2Discard`: スレーブが通信ステップのサブインターバルのみを正常に計算した場合
  * `fmi2Error`: 通信ステップを全く実行できなかった場合
  * `fmi2Fatal`: FMUを不可逆的に破損させるエラーが発生した場合
  * `fmi2Pending`: スレーブが非同期に関数を実行している場合にこのステータスが返されます

# 出典

  * FMISpec2.0.2 リンク: [https://fmi-standard.org/](https://fmi-standard.org/)
  * FMISpec2.0.2[p.16]: 2.1.2 プラットフォーム依存の定義 (fmi2TypesPlatform.h)
  * FMISpec2.0.2[p.16]: 2.1.3 関数によって返されるステータス
  * FMISpec2.0.2[p.83]: 3.2.2 モデル方程式の評価

また、[`fmi2EnterContinuousTimeMode`](@ref)も参照してください。
