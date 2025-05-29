```
fmi3GetEventIndicators!(c::FMU3Instance, eventIndicators::AbstractArray{fmi3Float64}, ni::Csize_t)
```

現在の時間瞬間と現在の状態におけるイベントインジケーターを計算します。EventIndicatorsは、その符号の変化によってイベントを示します。

# 引数

  * `c::FMU3Instance`: ミュータブル構造体で、FMI 3.0標準におけるFMUのインスタンス化されたインスタンスを表します。
  * `eventIndicators::AbstractArray{fmi3Float64}`: 引数`eventIndicators`は、`Real`データ型のエイリアスタイプである`fmi3Float64`の値を含みます。`eventIndicators`は、イベントインジケーターを表すベクトルの`Real`値を含む`AbstractArray`です。
  * `ni::Csize_t`: 引数`ni`は、ベクトル`eventIndicators`の長さを定義し、チェック目的で提供されます。

# 戻り値

  * `status::fmi3Status`: 戻り値`status`は、`fmi3Status`型の列挙であり、関数呼び出しの成功を示します。

より詳細には：

  * `fmi3OK`: すべて正常
  * `fmi3Warning`: いくつかの問題があるが、計算は続行できる
  * `fmi3Discard`: スレーブが通信ステップのサブインターバルのみを正常に計算した場合
  * `fmi3Error`: 通信ステップを全く実行できなかった場合
  * `fmi3Fatal`: FMUを不可逆的に破損させるエラーが発生した場合

# ソース

  * FMISpec3.0 リンク: [https://fmi-standard.org/](https://fmi-standard.org/)
  * FMISpec3.0: 2.2.3 プラットフォーム依存の定義
  * FMISpec3.0: 2.2.4 関数によって返されるステータス
  * FMISpec3.0: 3.2.1. 状態: 連続時間モード

さらに[`fmi3GetEventIndicators!`](@ref)も参照してください。
