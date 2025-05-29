```
running_median!(mf::MedianFilter, output, input, tapering=:sym; nan=:include) -> output
```

`mf`を使用して`input`の移動中央値を計算し、結果を`output`に書き込みます。

詳細については、[`running_median`](@ref)を参照してください。

# 例

```jldoctest
input = [4 5 6;
         1 0 9;
         9 8 7;
         3 1 2;]
output = similar(input, (4,3))
mf = MedianFilter(eltype(input), 3)
for j in axes(input, 2) # 各列に対して移動中央値を計算
    # 各イテレーションでmfを再利用
    running_median!(mf, @view(output[:,j]), input[:,j])
end
output

# output
4×3 Matrix{Int64}:
 4  5  6
 4  5  7
 3  1  7
 3  1  2
```
