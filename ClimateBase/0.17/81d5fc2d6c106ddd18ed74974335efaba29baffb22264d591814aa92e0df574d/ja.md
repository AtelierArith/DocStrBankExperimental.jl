```
spatialidxs(A::ClimArray) → idxs
```

`A`のすべての空間ポイントにアクセスするために使用できる反復可能なオブジェクトを返します。構文は次のとおりです。

```julia
idxs = spatialidxs(A)
for i in idxs
    slice_at_give_space_point = A[i...]
end
```

すべてのタイプの空間で機能します（`...`は`i`が`Tuple`であるため必要です）。
