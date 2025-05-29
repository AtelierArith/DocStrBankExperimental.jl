```
p6est_connectivity_new(conn4, top_vertices, height)
```

[`p6est_connectivity_t`](@ref)を[`p4est_connectivity_t`](@ref)から作成します。すべてのフィールドがコピーされるため、すべての入力は安全に破棄できます。

### パラメータ

  * `conn4`:[in] 2D接続性
  * `top_vertices`:[in] NULLの場合、シートは均一な垂直プロファイルを持ちます。それ以外の場合、*top_vertices*はシートの上部の頂点を示します。*conn4*->tree*to*vertexと同じサイズである必要があります。
  * `height`:[in] *top_vertices* == NULLの場合、これはシートの底から上部までのオフセットを示します。

### 戻り値

2D+1D接続性情報。

### プロトタイプ

```c
p6est_connectivity_t *p6est_connectivity_new (p4est_connectivity_t * conn4, double *top_vertices, double height[3]);
```
