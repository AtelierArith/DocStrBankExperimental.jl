```
fmi3GetUInt8!(c::FMU3Instance, vr::fmi3ValueReferenceFormat, values::AbstractArray{fmi3UInt8})
```

指定されたフィールドに変数の配列の整数値を書き込みます。

fmi3GetUInt8!は値の配列に対してのみ可能です。スカラーの代わりに配列を使用してください。

# 引数

  * `c::FMU3Instance`: FMU 3.0標準におけるインスタンス化されたFMUのインスタンスを表す可変構造体。
  * `vr::fmi3ValueReferenceFormat`: ユーザーがfmi[X]ValueReferenceを渡す方法のワイルドカード

詳細: `fmi3ValueReferenceFormat = Union{Nothing, String, Array{String,1}, fmi3ValueReference, Array{fmi3ValueReference,1}, Int64, Array{Int64,1}, Symbol}`

  * `values::AbstractArray{fmi3UInt8}`: 引数`values`は、これらの変数の実際の値を持つAbstractArrayです。

# 戻り値

  * `status::fmi3Status`: 戻り値`status`は`fmi3Status`型の列挙で、関数呼び出しの成功を示します。

詳細:

  * `fmi3OK`: すべて正常
  * `fmi3Warning`: いくつかの問題があるが、計算は続行できる
  * `fmi3Discard`: スレーブが通信ステップのサブインターバルのみを正常に計算した場合
  * `fmi3Error`: 通信ステップを全く実行できなかった場合
  * `fmi3Fatal`: FMUを不可逆的に破損させるエラーが発生した場合

# 出典

  * FMISpec3.0 リンク: [https://fmi-standard.org/](https://fmi-standard.org/)
  * FMISpec3.0: 2.2.4 関数によって返されるステータス
  * FMISpec3.0: 2.2.6.2. 変数の値の取得と設定

また[`fmi3GetUInt8!`](@ref)も参照してください。
