```
lattice(V::AbstractSpace, gens::Vector) -> AbstractLat
```

与えられた環境空間 `V` と生成子のリスト `gens` に対して、`gens` によって張られた格子を `V` 内で返します。`V` がエルミート（または二次）である場合、出力はエルミート（または二次）格子になります。

`gens` が空の場合、関数は `V` 内のゼロ格子を返します。
