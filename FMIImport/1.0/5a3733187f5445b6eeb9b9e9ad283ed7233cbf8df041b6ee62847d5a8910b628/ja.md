```
fmi3GetContinuousStateDerivatives!(c::FMU3Instance,
                        derivatives::AbstractArray{fmi3Float64},
                        nx::Csize_t)
```

現在の時間瞬間と現在の状態における状態導関数を計算します。

# 引数

  * `c::FMU3Instance`: ミュータブル構造体で、FMI 3.0 標準における FMU のインスタンス化されたインスタンスを表します。
  * `derivatives::AbstractArray{fmi3Float64}`: 引数 `derivatives` には、`Real` データ型のエイリアスタイプである `fmi3Float64` の値が含まれています。`derivatives` は、導関数を表すベクトルの `Real` 値を含む `AbstractArray` です。導関数ベクトルの要素の順序は、状態ベクトルの順序と同じです。
  * `nx::Csize_t`: 引数 `nx` は、ベクトル `derivatives` の長さを定義し、チェック目的で提供されます。

# 戻り値

  * `status::fmi3Status`: 戻り値 `status` は、`fmi3Status` 型の列挙体で、関数呼び出しの成功を示します。

より詳細には：

  * `fmi3OK`: 問題なし
  * `fmi3Warning`: いくつかの問題があるが、計算は続行可能
  * `fmi3Discard`: スレーブが通信ステップのサブインターバルのみを正常に計算した場合
  * `fmi3Error`: 通信ステップを全く実行できなかった場合
  * `fmi3Fatal`: FMU を不可逆的に破損させるエラーが発生した場合

# ソース

  * FMISpec3.0 リンク: [https://fmi-standard.org/](https://fmi-standard.org/)
  * FMISpec3.0: 2.2.3 プラットフォーム依存の定義
  * FMISpec3.0: 2.2.4 関数によって返されるステータス
  * FMISpec3.0: 3.2.1. 状態: 連続時間モード

さらに [`fmi3GetContinuousStateDerivatives!`](@ref) を参照してください。
