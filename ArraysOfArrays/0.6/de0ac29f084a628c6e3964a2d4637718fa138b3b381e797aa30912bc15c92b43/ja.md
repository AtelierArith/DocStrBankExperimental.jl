```
flatview(A::ArrayOfSimilarArrays{T,M,N,L,P})::P
```

`A` によってラップされた次元 `L = M + N` の配列を返します。結果の形状は、`A` の内部の一貫性を壊すことなく自由に変更できます。
