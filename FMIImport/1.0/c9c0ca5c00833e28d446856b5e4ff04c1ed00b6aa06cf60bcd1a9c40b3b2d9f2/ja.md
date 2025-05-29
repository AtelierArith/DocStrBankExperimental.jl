```
fmi3GetContinuousStates!(c::FMU3Instance, nominals::AbstractArray{fmi3Float64}, nContinuousStates::Csize_t)
```

現在の時間瞬間での状態を返します。

この関数は、`fmi3UpdateDiscreteStates` が `valuesOfContinuousStatesChanged == fmi3True` で返された場合に呼び出す必要があります。コシミュレーションおよびスケジュール実行では許可されていません。

# 引数

  * `c::FMU3Instance`: ミュータブル構造体で、FMI 2.0.2 標準の FMU のインスタンス化されたインスタンスを表します。
  * `nominals::AbstractArray{fmi3Float64}`: 引数 `nominals` には、`Real` データ型のエイリアスタイプである `fmi3Float64` の値が含まれています。`nominals` は、新しい状態ベクトルを表すベクトルの `Real` 値を含む `AbstractArray` です。
  * `nContinuousStates::Csize_t`: 引数 `nContinuousStates` は、ベクトル `nominals` の長さを定義し、チェック目的で提供されます。

# 戻り値

  * `status::fmi3Status`: 戻り値 `status` は `fmi3Status` 型の列挙体で、関数呼び出しの成功を示します。

より詳細には：

  * `fmi3OK`: 問題なし
  * `fmi3Warning`: いくつかの問題があるが、計算は続行できる
  * `fmi3Discard`: スレーブが通信ステップのサブインターバルのみを正常に計算した場合
  * `fmi3Error`: 通信ステップを全く実行できなかった場合
  * `fmi3Fatal`: FMU を不可逆的に破損させるエラーが発生した場合

# ソース

  * FMISpec3.0 リンク: [https://fmi-standard.org/](https://fmi-standard.org/)
  * FMISpec3.0: 2.2.3 プラットフォーム依存の定義
  * FMISpec3.0: 2.2.4 関数によって返されるステータス
  * FMISpec3.0: 2.3.3. 状態: 初期化モード

[`fmi3GetContinuousStates!`](@ref) も参照してください。
