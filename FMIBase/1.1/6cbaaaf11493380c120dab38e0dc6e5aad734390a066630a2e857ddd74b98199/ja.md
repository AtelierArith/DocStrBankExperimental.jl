```
getValue!(comp::FMU2Component, vrs::fmi2ValueReferenceFormat, dst::AbstractArray)
```

参照 `vrs` の値を取得し、`dst` に格納します。

# 引数

  * `comp::FMU2Component`: FMU 2.0.2 標準におけるインスタンス化された FMU のインスタンスを表す可変構造体。
  * `vrs::fmi2ValueReferenceFormat`: ユーザーが fmi[X]ValueReference を渡す方法のワイルドカード。
  * `dst::AbstractArray`: 目的地の配列で、値参照のデータ型と一致する必要があります。

# 戻り値

  * `retcodes::Array{fmi2Status}`: 型 `fmi2Status` の長さ length(vrs) の配列を返します。型 `fmi2Status` は列挙型で、関数呼び出しの成功を示します。
