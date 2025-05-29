```
fmi3SetContinuousStates(c::FMU3Instance,
    x::AbstractArray{fmi3Float64},
    nx::Csize_t)
```

新しい（連続）状態ベクトルを設定し、状態に依存する変数のキャッシュを再初期化します。引数 nx はベクトル x の長さであり、チェック目的で提供されます。

`fmi3UpdateDiscreteStates` が `nominalsOfContinuousStatesChanged == fmi3True` で返された場合、状態の少なくとも1つの名目値が変更されており、`fmi3GetNominalsOfContinuousStates` で照会できます。コシミュレーションおよびスケジュール実行では許可されていません。

# 引数

  * `c::FMU3Instance`: ミュータブル構造体で、FMI 2.0.2 標準の FMU のインスタンス化されたインスタンスを表します。
  * `x::AbstractArray{fmi3Float64}`: 引数 `x` には、`fmi3Float64` 型の値が含まれており、これは `Real` データ型のエイリアスタイプです。`x` は、連続状態の名目値を表すベクトルの `Real` 値を含む `AbstractArray` です。
  * `nx::Csize_t`: 引数 `nx` はベクトル `x` の長さを定義し、チェック目的で提供されます。

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
  * FMISpec3.0: 3.2.1. 状態: 連続時間モード

また、[`fmi3SetContinuousStates`](@ref) も参照してください。
