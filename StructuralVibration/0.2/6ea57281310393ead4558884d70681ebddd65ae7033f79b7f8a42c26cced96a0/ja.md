```
SdofFrequencyProblem(sdof, F, type_exc, type_resp)
```

sdofシステムの周波数応答を計算するためのデータを含む構造体

**フィールド**

  * `sdof::Sdof`: Sdof構造体
  * `F::AbstractVector`: 力の励起 [N] または基底の動き [m] のベクトル
  * `freq::AbstractRange`: 周波数 [Hz] のベクトル
  * `type_exc::Symbol`: 励起のタイプ

      * `:force`: 外部力（デフォルト）
      * `:base`: 基底の動き
  * `type_resp::Symbol`: 応答のタイプ

      * `:dis`: 変位スペクトル（デフォルト）
      * `:vel`: 速度スペクトル
      * `:acc`: 加速度スペクトル
