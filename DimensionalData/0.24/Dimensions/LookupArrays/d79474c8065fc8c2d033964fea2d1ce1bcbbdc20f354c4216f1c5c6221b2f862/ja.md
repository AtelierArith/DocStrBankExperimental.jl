```
At <: IntSelector

At(x, atol, rtol)
At(x; atol=nothing, rtol=nothing)
```

渡された次元で値と正確に一致するセレクタ、またはエラーをスローします。範囲や配列の場合、すべての中間値は既存の値と一致しなければなりません - 端点だけではありません。

`x` は任意の値または値の `Vector` です。

`atol` と `rtol` は `isapprox` に渡されます。`Number` の場合、`rtol` は `Base.rtoldefault` に設定され、それ以外の場合は `nothing` となり、使用されません。

## 例

```jldoctest
using DimensionalData

A = DimArray([1 2 3; 4 5 6], (X(10:10:20), Y(5:7)))
A[X(At(20)), Y(At(6))]

# 出力

5
```
