```
vcount([f=identity,] A::AbstractArray, dims=:)
```

`f` が真を返す `A` の要素の数を指定された `dims` にわたってカウントします。`f` が省略された場合、`A` の `true` 要素の数をカウントします（これは `AbstractArray{Bool}` である必要があります）。
