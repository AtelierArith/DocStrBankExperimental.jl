```
fmi2GetDerivatives!(c::FMU2Component, derivatives::AbstractArray{fmi2Real})
```

現在の時間瞬間と現在の状態における状態の導関数を計算します。

# 引数

  * `c::FMU2Component`: FMI 2.0.2標準におけるFMUのインスタンス化されたインスタンスを表す可変構造体。
  * `derivatives::Array{fmi2Real}`: 現在の状態の`derivatives`を表す`fmi2Real`値を格納します。導関数ベクトルの要素の順序は、状態ベクトルの順序と同じです。

# 戻り値

  * `status::fmi2Status`: 戻り値`status`は`fmi2Status`型の列挙であり、関数呼び出しの成功を示します。

より詳細には：

  * `fmi2OK`: すべて正常
  * `fmi2Warning`: いくつかの問題があるが、計算は続行できる
  * `fmi2Discard`: スレーブが通信ステップのサブインターバルのみを正常に計算した場合
  * `fmi2Error`: 通信ステップを全く実行できなかった場合
  * `fmi2Fatal`: FMUを不可逆的に破損させるエラーが発生した場合
  * `fmi2Pending`: スレーブが非同期に関数を実行する場合にこのステータスが返される

# 出典

  * FMISpec2.0.2 リンク: [https://fmi-standard.org/](https://fmi-standard.org/)
  * FMISpec2.0.2[p.16]: 2.1.2 プラットフォーム依存の定義 (fmi2TypesPlatform.h)
  * FMISpec2.0.2[p.16]: 2.1.3 関数によって返されるステータス
  * FMISpec2.0.2[p.83]: 3.2.2 モデル方程式の評価

また[`fmi2GetDerivatives!`](@ref)も参照してください。
