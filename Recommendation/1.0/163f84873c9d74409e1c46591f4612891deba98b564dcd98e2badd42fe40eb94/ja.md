```
onehot(value, value_set::AbstractVector) -> Vector{Float64}
```

カテゴリカル値をワンホットエンコードされたベクトルにエンコードします。値は、`Integer`または`String`型の`value_set`の要素の1つでなければなりません。`missing`または`nothing`も値として受け入れられますが、それらはゼロベクトルに変換されます。
