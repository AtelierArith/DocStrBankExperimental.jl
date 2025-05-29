```
has_standard_indexing(A)
```

は、`A` のインデックスがすべての軸で 1 から始まる場合に `true` を返します。複数の引数で呼び出すことができます：

```
has_standard_indexing(A, B, ...)
```

は次のように同等です：

```
has_standard_indexing(A) && has_standard_indexing(B) && ...
```

`Base.has_offset_axes` の反対であり、Julia の 0.7 より古いバージョンでは利用できません。
