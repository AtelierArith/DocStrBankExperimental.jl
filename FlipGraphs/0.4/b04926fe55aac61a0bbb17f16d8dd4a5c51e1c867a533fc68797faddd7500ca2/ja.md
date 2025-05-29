```
matrix_equal(A::Matrix{Int}, B::Matrix{Int}) :: Bool
```

`A`が`B`と等しい場合は`true`を返します。

この関数は`A==B`を呼び出すよりもはるかに速いです。ただし、`A`と`B`は同じ次元を持つと仮定されています。
