```
add!(tree::VoronoiTree, v, id, tol)
```

木に点 `v` を識別子 `id` で挿入します。もし `search_in_radius(tree, v, tol)` が `nothing` の場合、タプル `(id, true)` が返されます。そうでない場合は、取得した識別子と `false` が返されます。
