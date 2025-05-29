```
p6est_new_from_p4est(p4est_, top_vertices, height, min_zlevel, data_size, init_fn, user_pointer)
```

既に作成された `p4est` から列を表す新しいフォレストを作成します。

### パラメータ

  * `p4est`:[in] 有効な `p4est`。ディープコピーが作成されるため、これを破棄しても新しい `p6est` オブジェクトには影響しません。
  * `top_vertices`:[in] `p6est_conectivity_new()` と同じです。
  * `height`:[in] `p6est_conectivity_new()` と同じです。
  * `min_zlevel`:[in] [`p6est_new`](@ref)() と同じです。
  * `data_size`:[in] [`p6est_new`](@ref)() と同じです。
  * `init_fn`:[in] [`p6est_new`](@ref)() と同じです。
  * `user_pointer`:[in] [`p6est_new`](@ref)() と同じです。

### 戻り値

これは有効なフォレストを返します。ユーザーは新しい `p6est` の接続性を独立して破棄する必要があります。

### プロトタイプ

```c
p6est_t *p6est_new_from_p4est (p4est_t * p4est, double *top_vertices, double height[3], int min_zlevel, size_t data_size, p6est_init_t init_fn, void *user_pointer);
```
