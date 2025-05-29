```
fmi3GetNominalsOfContinuousStates!(c::FMU3Instance, x_nominal::AbstractArray{fmi3Float64}, nx::Csize_t)
```

連続状態の名目値を返します。

`fmi3UpdateDiscreteStates` が `nominalsOfContinuousStatesChanged == fmi3True` で返された場合、状態の少なくとも1つの名目値が変更されており、`fmi3GetNominalsOfContinuousStates` で照会できます。コシミュレーションおよびスケジュール実行では許可されていません。

# 引数

  * `c::FMU3Instance`: ミュータブル構造体で、FMI 2.0.2標準のFMUのインスタンス化されたインスタンスを表します。
  * `x_nominal::AbstractArray{fmi3Float64}`: 引数 `x_nominal` には、`Real` データ型のエイリアスタイプである `fmi3Float64` の値が含まれています。`x_nominal` は、連続状態の名目値を表すベクトルの `Real` 値を含む `AbstractArray` です。
  * `nx::Csize_t`: 引数 `nx` は、ベクトル `x_nominal` の長さを定義し、チェック目的で提供されます。

# 戻り値

  * `status::fmi3Status`: 戻り値 `status` は `fmi3Status` 型の列挙型で、関数呼び出しの成功を示します。

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
  * FMISpec3.0: 2.3.3. 状態: 初期化モード

また [`fmi3GetNominalsOfContinuousStates!`](@ref) を参照してください。
