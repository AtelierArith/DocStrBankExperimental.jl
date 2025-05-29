```
DynamicStyle(env::AbstractEnv) = SEQUENTIAL
```

[`NumAgentStyle`](@ref) が [`MultiAgent`](@ref) の環境でのみ有効です。プレイヤーが同時にプレイできるかどうかを判断します。可能な戻り値は次のとおりです。

  * [`SEQUENTIAL`](@ref)。これがデフォルトの戻り値です。
  * [`SIMULTANEOUS`](@ref)。
