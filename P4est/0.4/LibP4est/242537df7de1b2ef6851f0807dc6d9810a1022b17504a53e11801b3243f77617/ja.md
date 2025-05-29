```
p8est_search(p4est_, quadrant_fn, point_fn, points)
```

この関数は後方互換性のために提供されています。call_post = 0でp8est*search*localを呼び出します。

### プロトタイプ

```c
void p8est_search (p8est_t * p4est, p8est_search_query_t quadrant_fn, p8est_search_query_t point_fn, sc_array_t * points);
```
