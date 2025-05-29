```
struct NoOptimizer <: Exception end
```

最適化器が設定されていません。最適化器は[`Model`](@ref)コンストラクタに提供するか、[`set_optimizer`](@ref)を呼び出すことで設定できます。
