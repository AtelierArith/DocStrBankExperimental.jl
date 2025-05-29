```
dual(V::VectorSpace) -> VectorSpace
```

ベクトル空間 `V` の双対空間を返します。これは `V'` を介しても得られます。これは `dual(dual(V)) == V` を満たすべきです。`typeof(V) == typeof(V')` であると仮定されています。
