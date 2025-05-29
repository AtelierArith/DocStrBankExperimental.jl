```
hessian(f::Function, v::Union{SecondOrderTensor, Vec, Number})
hessian(f::Function, v::Union{SecondOrderTensor, Vec, Number}, :all)
```

入力関数のヘッセ行列を計算します。 (擬似)キーワード `all` が指定された場合、関数の低次の結果（勾配と値）も第2および第3の出力引数として返されます。

# 例

```jldoctest
julia> A = rand(SymmetricTensor{2, 2});

julia> ∇∇f = hessian(norm, A)
2×2×2×2 SymmetricTensor{4, 2, Float64, 9}:
[:, :, 1, 1] =
  0.988034  -0.271765
 -0.271765  -0.108194

[:, :, 2, 1] =
 -0.271765   0.11695
  0.11695   -0.182235

[:, :, 1, 2] =
 -0.271765   0.11695
  0.11695   -0.182235

[:, :, 2, 2] =
 -0.108194  -0.182235
 -0.182235   1.07683

julia> ∇∇f, ∇f, f = hessian(norm, A, :all);
```
