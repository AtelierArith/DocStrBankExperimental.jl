```julia
struct RegistryError <: Exception
```

特定のインターフェースに対して特定の型 `target_type` を登録できない場合に発生する例外であり、関数 `func` を実装する必要があります。

# フィールド

  * `func::Function`
  * `target_type::Any`
