```
fmi3EnterContinuousTimeMode(c::FMU3Instance; soft::Bool=false)
```

モデルは連続時間モードに入り、すべての離散時間方程式は非アクティブになり、すべての関係は「凍結」されます。この関数は、イベントモードから連続時間モードに変更する際に呼び出す必要があります（すべての関与するFMUおよび他のモデルにおけるイベントモードでのグローバルイベント反復が収束した後）。

# 引数

  * `c::FMU3Instance`: ミュータブル構造体で、FMI 3.0標準におけるFMUのインスタンス化されたインスタンスを表します。

# キーワード

  * `soft::Bool=false`: キーワード `soft = true` の場合、`fmi3Teminate` は状態 `fmi3InstanceStateContinuousTimeMode` または `fmi3InstanceStateEventMode` で呼び出す必要があります。

# 戻り値

  * `status::fmi3Status`: 戻り値 `status` は `fmi3Status` 型の列挙であり、関数呼び出しの成功を示します。

より詳細には：

  * `fmi3OK`: すべて正常
  * `fmi3Warning`: 物事は完全ではないが、計算は続行可能
  * `fmi3Discard`: スレーブが通信ステップのサブインターバルのみを正常に計算した場合
  * `fmi3Error`: 通信ステップを全く実行できなかった場合
  * `fmi3Fatal`: FMUを不可逆的に破損させるエラーが発生した場合

# ソース

  * FMISpec3.0 リンク: [https://fmi-standard.org/](https://fmi-standard.org/)
  * FMISpec3.0: 2.2.3 プラットフォーム依存の定義
  * FMISpec3.0: 2.2.4 関数によって返されるステータス
  * FMISpec3.0: 2.3.5. 状態: イベントモード

さらに [`fmi3EnterContinuousTimeMode`](@ref) を参照してください。
