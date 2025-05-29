```
p4est_search(p4est_, quadrant_fn, point_fn, points)
```

この関数は後方互換性のために提供されています。call_post = 0でp4est*search*localを呼び出します。

### プロトタイプ

```c
void p4est_search (p4est_t * p4est, p4est_search_query_t quadrant_fn, p4est_search_query_t point_fn, sc_array_t * points);
```
