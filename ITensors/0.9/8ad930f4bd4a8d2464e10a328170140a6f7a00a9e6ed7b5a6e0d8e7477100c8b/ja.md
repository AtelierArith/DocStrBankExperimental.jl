```
getindex(T::ITensor, ivs...)
```

ITensorの指定された要素を取得します。`IndexVal`または`Pair{<:Index, Int}`のリストを使用します。

# 例

```julia
i = Index(2; tags = "i")
A = ITensor(2.0, i, i')
A[i => 1, i' => 2] # 2.0, 同じく: A[i' => 2, i => 1]
```
