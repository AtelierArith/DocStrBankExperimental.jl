```
FreeParameter
FreeParameter(name::Symbol) -> FreeParameter
```

自由パラメータを表す構造体で、これはパラメータ化された [`Gate`](@ref) または [`Noise`](@ref) を初期化するために使用され、その後 [`Circuit`](@ref) へのマッピングを提供することで固定値を与えることができます。
