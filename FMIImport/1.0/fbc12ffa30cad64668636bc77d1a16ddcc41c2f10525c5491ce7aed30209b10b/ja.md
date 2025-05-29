```
fmi3SetBinary(c::FMU3Instance, vr::fmi3ValueReferenceFormat, valueSizes::Union{AbstractArray{Csize_t}, Csize_t}, values::Union{AbstractArray{fmi3Binary}, fmi3Binary})
```

バイナリ変数の配列の値を設定します

# 引数

  * `c::FMU3Instance`: ミュータブル構造体で、FMI 3.0 標準における FMU のインスタンス化されたインスタンスを表します。
  * `vr::fmi3ValueReferenceFormat`: ユーザーが fmi[X]ValueReference を渡す方法のワイルドカード

詳細: `fmi3ValueReferenceFormat = Union{Nothing, String, Array{String,1}, fmi3ValueReference, Array{fmi3ValueReference,1}, Int64, Array{Int64,1}, Symbol}`

  * `valueSizes::Union{AbstractArray{Csize_t}, Csize_t}`: 引数 `valueSizes` は各変数のバイナリ要素のサイズを定義します。
  * `values::Union{AbstractArray{fmi3Binary}, fmi3Binary}`: 引数 `values` はこれらの変数の実際の値を持つ AbstractArray です。

# 戻り値

  * `status::fmi3Status`: 戻り値 `status` は `fmi3Status` 型の列挙で、関数呼び出しの成功を示します。

詳細:

  * `fmi3OK`: すべて正常
  * `fmi3Warning`: いくつかの問題があるが、計算は続行できる
  * `fmi3Discard`: スレーブが通信ステップのサブインターバルのみを正常に計算した場合
  * `fmi3Error`: 通信ステップを全く実行できなかった場合
  * `fmi3Fatal`: FMU を不可逆的に破損させるエラーが発生した場合

# ソース

  * FMISpec3.0 リンク: [https://fmi-standard.org/](https://fmi-standard.org/)
  * FMISpec3.0: 2.2.4 関数によって返されるステータス
  * FMISpec3.0: 2.2.6.2. 変数の値の取得と設定

また、[`fmi3SetBinary`](@ref)も参照してください。
