```
Result(val::T, exception_type::Type{E}=Exception) -> Result{T, E}
```

型 `T` の値または型 `E` の例外を保持できる `Result` を作成し、そこに `val` を格納します。例外の型が指定されていない場合、スーパークラス `Exception` が `E` として使用されます。
