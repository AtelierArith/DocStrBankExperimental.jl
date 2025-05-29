```
bulksearch(ss, queries, t::SearchType [, skip]; kwargs... ) → vec_of_idxs, vec_of_ds
```

[`search`](@ref) と同様ですが、多くの入力クエリポイントに対して多くの検索が行われます。

この場合、`skip` は二つの引数 `skip(i, j)` を取ります。ここで `j` は現在検索しているクエリのインデックスであり（`j` は `queries` のインデックスで、1 から `length(queries)` までの範囲です）。
