```
@critical expr
```

アサーション `expr` の失敗時にテストケースを終了します。`expr` は [`@test`](@ref)、[`@test_fail`](@ref)、[`@test_throws`](@ref)、[`@test_broken`](@ref)、[`@inferred`](@ref)、[`@test_warn`](@ref)、[`@test_nowarn`](@ref) のいずれかから始まる必要があります。
