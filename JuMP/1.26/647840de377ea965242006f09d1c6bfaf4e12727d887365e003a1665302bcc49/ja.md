```
struct NoOptimizer <: Exception end
```

最適化プログラムが設定されておらず、必要な場合にスローされるエラーです。

最適化プログラムは[`Model`](@ref)コンストラクタに提供するか、[`set_optimizer`](@ref)を呼び出すことで設定できます。

## 例

```jldoctest
julia> model = Model();

julia> optimize!(model)
ERROR: NoOptimizer()
Stacktrace:
[...]
```
