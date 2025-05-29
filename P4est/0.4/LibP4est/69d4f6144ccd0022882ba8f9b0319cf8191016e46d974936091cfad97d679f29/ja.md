```
p8est_find_range_boundaries(lq, uq, level, faces, edges, corners)
```

範囲の四分木に触れる境界点を見つけます。

最初と最後の四分木を示す2つの最小四分木、**lq**と**uq**が与えられたとき、範囲が触れる木の境界の部分を特定します。

### パラメータ

  * `lq`:[in] 範囲の開始時の最小四分木: NULLの場合、木の最初の四分木が範囲の開始と見なされます。
  * `uq`:[in] 範囲の終了時の最小四分木: NULLの場合、木の最後の四分木が範囲の終了と見なされます。
  * `level`:[in] 境界がテストされる含む四分木のレベル: 木全体の境界をテストしたい場合は0を指定します。
  * `faces`:[in,out] サイズ6の配列で、埋められます: faces[i]は範囲がその面に触れる場合はtrueです。
  * `edges`:[in,out] サイズ12の配列で、埋められます: edges[i]は範囲がその辺に触れる場合はtrueです。
  * `corners`:[in,out] サイズ8の配列で、埋められます: corners[i]は範囲がそのコーナーに触れる場合はtrueです。**faces**、**edges**、または**corners**はNULLである可能性があります。

### 戻り値

**faces**、**edges**、および**corners**の同じ情報でエンコードされたint32_tを返します: 最初の（最小の）6ビットは6つの面を表し、次の12ビットは12の辺を表し、次の8ビットは8つのコーナーを表します。

### プロトタイプ

```c
int32_t p8est_find_range_boundaries (p8est_quadrant_t * lq, p8est_quadrant_t * uq, int level, int faces[], int edges[], int corners[]);
```
