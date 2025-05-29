```
LinearOperator(type::Type{T}, nrow, ncol, symmetric, hermitian, prod!,
                [tprod!=nothing, ctprod!=nothing],
                S = Vector{T}) where {T}
```

関数から線形演算子を構築します。型は最初の引数として指定されます。`S`をGPU上のLinearOperatorsを使用するように変更します。線形演算子は型を強制しないため、間違った型を使用するとエラーが発生する可能性があります。例えば、

```
A = [im 1.0; 0.0 1.0] # 複素行列
function mulOp!(res, M, v, α, β)
  mul!(res, M, v, α, β)
end
op = LinearOperator(Float64, 2, 2, false, false, 
                    (res, v, α, β) -> mulOp!(res, A, v, α, β), 
                    (res, u, α, β) -> mulOp!(res, transpose(A), u, α, β), 
                    (res, w, α, β) -> mulOp!(res, A', w, α, β))
Matrix(op) # InexactError
```

エラーは、`Matrix(op)`が複素行列`A`の内容を持つFloat64行列を作成しようとするために発生します。

`*`を使用すると、`NaN`値を含むベクトルが生成される可能性があります。これは、`Vector{Float64}(undef, n)`のような事前に割り当てられたベクトルを使用して3引数の`mul!`関数を使用した場合にも発生する可能性があります。この問題を解決するには、`β == 0`と`β != 0`のケースを別々に処理する必要があります：

```
d1 = [2.0; 3.0]
function mulSquareOpDiagonal!(res, d, v, α, β::T) where T
  if β == zero(T)
    res .= α .* d .* v
  else 
    res .= α .* d .* v .+ β .* res
  end
end
op = LinearOperator(Float64, 2, 2, true, true, 
                    (res, v, α, β) -> mulSquareOpDiagonal!(res, d, v, α, β))
```

3引数の`mul!`を使用して演算子を作成することも可能です。この場合、5引数の`mul!`を使用するとストレージベクトルが生成されます。

```
A = rand(2, 2)
op = LinearOperator(Float64, 2, 2, false, false, 
                    (res, v) -> mul!(res, A, v),
                    (res, w) -> mul!(res, A', w))
```

3引数の`mul!`は、行列に演算子を適用する際にも機能します。 ```
