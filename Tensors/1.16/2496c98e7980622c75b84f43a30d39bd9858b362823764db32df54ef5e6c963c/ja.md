```
gradient(f::Function, v::Union{SecondOrderTensor, Vec, Number})
gradient(f::Function, v::Union{SecondOrderTensor, Vec, Number}, :all)
```

入力関数の勾配を計算します。 (擬似)キーワード `all` が与えられた場合、関数の値も2番目の出力引数として返されます。

# 例

```jldoctest
julia> A = rand(SymmetricTensor{2, 2});

julia> ∇f = gradient(norm, A)
2×2 SymmetricTensor{2, 2, Float64, 3}:
 0.374672  0.63107
 0.63107   0.25124

julia> ∇f, f = gradient(norm, A, :all);
```
