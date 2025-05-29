```
parameterseries(P::Process; p=nothing, times_kwargs...)
```

[`Process`](@ref) のプロファイルを、[`times`](@ref) で指定された時間インデックスのパラメータ値として返します。`p` は返すパラメータのインデックスを指定します（例：1 または [2, 3]）。`p` がベクトルの場合、値は nₚ×nₜ 行列で返されます。
