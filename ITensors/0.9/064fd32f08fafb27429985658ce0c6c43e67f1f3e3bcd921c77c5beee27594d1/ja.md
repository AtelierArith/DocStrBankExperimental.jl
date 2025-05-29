```
getindex(T::ITensor, I::Int...)
```

ITensorの指定された要素を取得します。ITensorの内部インデックス順序を使用します。

# 例

```julia
i = Index(2; tags = "i")
A = ITensor(2.0, i, i')
A[1, 2] # 2.0, 同じく: A[i => 1, i' => 2]
```
