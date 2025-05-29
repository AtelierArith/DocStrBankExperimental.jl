```
CompositeManifoldError{T} <: Exception
```

発生したエラーのセットを収集するための複合型です。主に[`ComponentManifoldError`](@ref)と組み合わせて使用され、発生したエラーのセットを格納します。

# フィールド

  * `errors` `<:Exceptions`の`Vector`。
