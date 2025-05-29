```
fmi3EnterEventMode(c::FMU3Instance, stepEvent::Bool, stateEvent::Bool, rootsFound::AbstractArray{fmi3Int32}, nEventIndicators::Csize_t, timeEvent::Bool)
```

モデルは、ModelExchangeの連続時間モードまたはCoSimulationのステップモードからイベントモードに入ります。離散時間方程式がアクティブになる可能性があり（関係は「凍結」されません）。

# TODO 引数

# 引数

  * `c::FMU3Instance`: FMU 3.0標準のインスタンス化されたFMUを表す可変構造体。
  * `stepEvent::Bool`:
  * `stateEvent::Bool`:
  * `rootsFound::AbstractArray{fmi3Int32}`:
  * `nEventIndicators::Csize_t`:
  * `timeEvent::Bool`:

# 戻り値

  * `status::fmi3Status`: 戻り値`status`は`fmi3Status`型の列挙で、関数呼び出しの成功を示します。

より詳細には：

  * `fmi3OK`: すべて正常
  * `fmi3Warning`: いくつかの問題があるが、計算は続行可能
  * `fmi3Discard`: スレーブが通信ステップのサブインターバルのみを正常に計算した場合
  * `fmi3Error`: 通信ステップを全く実行できなかった場合
  * `fmi3Fatal`: FMUを不可逆的に破損させるエラーが発生した場合

# ソース

  * FMISpec3.0 リンク: [https://fmi-standard.org/](https://fmi-standard.org/)
  * FMISpec3.0: 2.2.3 プラットフォーム依存の定義
  * FMISpec3.0: 2.2.4 関数によって返されるステータス
  * FMISpec3.0: 3.2.1. 状態: 連続時間モード

さらに[`fmi3EnterEventMode`](@ref)を参照してください。
