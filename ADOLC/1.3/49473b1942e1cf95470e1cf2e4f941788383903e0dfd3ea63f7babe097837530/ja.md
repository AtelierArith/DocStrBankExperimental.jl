```
create_cxx_identity(n::I_1, m::I_2) where {I_1 <: Integer, I_2 <: Integer}
```

CxxPtr{CxxPtr{Float64}} 型の形状 (`n`, `m`) の単位行列を作成します（C++ の double** のラッパー）。

# 例

```jldoctest
id = CxxMatrix(create_cxx_identity(2, 4), 2, 4)


# 出力

2×4 CxxMatrix:
 1.0  0.0  0.0  0.0
 0.0  1.0  0.0  0.0
```
