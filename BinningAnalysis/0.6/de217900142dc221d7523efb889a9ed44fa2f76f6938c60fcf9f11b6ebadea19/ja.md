```
IncrementBinner([::Type{T}; blocksize = 64])
IncrementBinner(zero_element::T[; blocksize = 64])
```

`zero_element` 数値型 `T` から `IncrementBinner` を作成します。

`IncrementBinner` にプッシュされた値は段階的に平均化されます。最初の `blocksize` 値がプッシュされるときは平均化は行われません。その後、`2blocksize` 要素が 2 つずつ平均化され、次に `4blocksize` 要素が 4 つずつ平均化されるなどします。これは、プッシュされた値が徐々に圧縮され、滑らかになることを意味します。
