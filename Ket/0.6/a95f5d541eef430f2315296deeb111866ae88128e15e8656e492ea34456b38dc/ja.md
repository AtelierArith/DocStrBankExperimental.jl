```
tensor_to_povm(A::Array{T,4}, o::Vector{Int})
```

共通のテンソル形式の測定セットを（エルミート）行列の行列に変換します。デフォルトでは、2番目の引数は`A`のサイズによって固定されます。結果が少ない測定がある場合は、カスタムの結果数を含めることもできます。
