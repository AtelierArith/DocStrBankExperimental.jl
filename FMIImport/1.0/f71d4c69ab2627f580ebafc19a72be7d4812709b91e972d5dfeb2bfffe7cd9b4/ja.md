```
fmiSetContinuousStates(c::FMU2Component,
                             x::Union{AbstractArray{Float32},AbstractArray{Float64}})
```

新しい（連続）状態ベクトルを設定し、状態に依存する変数のキャッシングを再初期化します。

# 引数

  * `c::FMU2Component`: FMU 2.0.2標準のインスタンス化されたFMUのインスタンスを表す可変構造体。
  * `x::Union{AbstractArray{Float32},AbstractArray{Float64}}`: 引数 `x` は `Float64` または `Float32` のベクトル値の `AbstractArray` です。

# 戻り値

  * `status::fmi2Status`: 戻り値 `status` は `fmi2Status` 型の列挙で、関数呼び出しの成功を示します。

より詳細には：

  * `fmi2OK`: すべて正常
  * `fmi2Warning`: いくつかの問題があるが、計算は続行できる
  * `fmi2Discard`: スレーブが通信ステップのサブインターバルのみを正常に計算した場合
  * `fmi2Error`: 通信ステップを全く実行できなかった場合
  * `fmi2Fatal`: FMUを不可逆的に破損させるエラーが発生した場合
  * `fmi2Pending`: スレーブが関数を非同期に実行する場合にこのステータスが返される

# 出典

  * FMISpec2.0.2 リンク: [https://fmi-standard.org/](https://fmi-standard.org/)
  * FMISpec2.0.2[p.16]: 2.1.2 プラットフォーム依存の定義 (fmi2TypesPlatform.h)
  * FMISpec2.0.2[p.16]: 2.1.3 関数によって返されるステータス
  * FMISpec2.0.2[p.83]: 3.2.1 独立変数の提供とキャッシングの再初期化

また、[`fmi2SetContinuousStates`](@ref)も参照してください。
