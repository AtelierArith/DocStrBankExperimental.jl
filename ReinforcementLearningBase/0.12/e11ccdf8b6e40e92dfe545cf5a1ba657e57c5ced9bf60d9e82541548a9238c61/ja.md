```
StateStyle(env::AbstractEnv)
```

`state(env)` の可能なスタイルを定義します。可能な値は次のとおりです：

  * [`Observation{T}`](@ref)。これがデフォルトの返り値です。
  * [`InternalState{T}`](@ref)
  * [`Information{T}`](@ref)
  * 必要に応じてカスタマイズされた状態スタイルを定義することもできます。

または、上記のいくつかを含むタプルです。

これは、複数の種類の状態を提供する環境に役立ちます。
