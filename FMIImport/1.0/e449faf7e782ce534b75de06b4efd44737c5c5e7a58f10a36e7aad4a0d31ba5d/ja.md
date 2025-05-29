```
fmi2GetEventIndicators!(c::FMU2Component, eventIndicators::AbstractArray{fmi2Real}, ni::Csize_t)
```

現在の時間瞬間と現在の状態におけるイベントインジケーターを計算します。

# 引数

  * `c::FMU2Component`: 可変構造体で、FMI 2.0.2 標準における FMU のインスタンス化されたインスタンスを表します。
  * `eventIndicators::AbstractArray{fmi2Real}`: 引数 `eventIndicators` には、`Real` データ型のエイリアスタイプである `fmi2Real` の値が含まれています。`eventIndicators` は、イベントインジケーターを表すベクトルの `Real` 値を含む `AbstractArray` です。
  * `ni::Csize_t`: 引数 `ni` は、ベクトル `eventIndicators` の長さを定義し、チェック目的で提供されます。

# 戻り値

  * `status::fmi2Status`: 戻り値 `status` は `fmi2Status` 型の列挙型で、関数呼び出しの成功を示します。

より詳細には：

  * `fmi2OK`: すべて正常
  * `fmi2Warning`: いくつかの問題があるが、計算は続行可能
  * `fmi2Discard`: スレーブが通信ステップのサブインターバルのみを正常に計算した場合
  * `fmi2Error`: 通信ステップを全く実行できなかった場合
  * `fmi2Fatal`: FMU を不可逆的に破損させるエラーが発生した場合
  * `fmi2Pending`: スレーブが関数を非同期に実行する場合にこのステータスが返されます。

# 出典

  * FMISpec2.0.2 リンク: [https://fmi-standard.org/](https://fmi-standard.org/)
  * FMISpec2.0.2[p.16]: 2.1.2 プラットフォーム依存の定義 (fmi2TypesPlatform.h)
  * FMISpec2.0.2[p.16]: 2.1.3 関数によって返されるステータス
  * FMISpec2.0.2[p.83]: 3.2.2 モデル方程式の評価

また [`fmi2GetEventIndicators!`](@ref) を参照してください。
