```
runs(arr::RunLengthArray{N,T})
```

ランレングス配列内の各ランの長さを含む `Array{N,1}` 型を返します。

```julia
x = RunLengthArray{Int,String}(["X", "X", "X", "O", "O"])
@assert runs(x) == Int[3, 2]
```

値のリストを取得するには、`values` を使用します。
