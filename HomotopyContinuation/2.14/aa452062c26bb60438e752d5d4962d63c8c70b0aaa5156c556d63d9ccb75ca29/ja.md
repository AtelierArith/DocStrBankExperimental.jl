```
add!(unique_points, v, id; atol = 1e-14, rtol = sqrt(eps()))
add!(unique_points, v, id, atol)
```

`unique_points` に点 `p` が含まれているかを検索し、`v` からの距離が `max(atol, norm(v)rtol)` 以下であるかを確認します。これが真であれば、`p` の識別子と `false` が返されます。そうでなければ `(id, true)` が返されます。
