```
fmi2GetDerivatives!(c::FMU2Component,
                   derivatives::AbstractArray{fmi2Real},
                   nx::Csize_t)
```

現在の時間瞬間および現在の状態における状態の導関数を計算します。

# 引数

  * `c::FMU2Component`: FMU 2.0.2標準におけるインスタンス化されたFMUのインスタンスを表す可変構造体。
  * `derivatives::AbstractArray{fmi2Real}`: 引数 `derivatives` には、`Real`データ型のエイリアスタイプである `fmi2Real` の値が含まれています。`derivatives` は導関数を表すベクトルの `Real` 値を含む `AbstractArray` です。導関数ベクトルの要素の順序は、状態ベクトルの順序と同じです。
  * `nx::Csize_t`: 引数 `nx` はベクトル `derivatives` の長さを定義し、チェック目的で提供されます。

# 戻り値

  * `status::fmi2Status`: 戻り値 `status` は `fmi2Status` 型の列挙型であり、関数呼び出しの成功を示します。

より詳細には：

  * `fmi2OK`: 問題なし
  * `fmi2Warning`: いくつかの問題があるが、計算は続行できる
  * `fmi2Discard`: スレーブが通信ステップのサブインターバルのみを正常に計算した場合
  * `fmi2Error`: 通信ステップを全く実行できなかった場合
  * `fmi2Fatal`: FMUを不可逆的に破損させるエラーが発生した場合
  * `fmi2Pending`: スレーブが関数を非同期に実行する場合にこのステータスが返されます

# 出典

  * FMISpec2.0.2 リンク: [https://fmi-standard.org/](https://fmi-standard.org/)
  * FMISpec2.0.2[p.16]: 2.1.2 プラットフォーム依存の定義 (fmi2TypesPlatform.h)
  * FMISpec2.0.2[p.16]: 2.1.3 関数によって返されるステータス
  * FMISpec2.0.2[p.83]: 3.2.2 モデル方程式の評価

[`fmi2GetDerivatives!`](@ref) も参照してください。
