```
p4est_find_range_boundaries(lq, uq, level, faces, corners)
```

範囲の四分木に触れる境界点を見つけます。

最小の二つの四分木、**lq** と **uq** が、四分木の範囲の最初と最後の四分木を示します。この範囲が木の境界のどの部分に触れるかを特定します。

### パラメータ

  * `lq`:[in] 範囲の開始時の最小の四分木: NULL の場合、木の最初の四分木が範囲の開始と見なされます。
  * `uq`:[in] 範囲の終了時の最小の四分木: NULL の場合、木の最後の四分木が範囲の終了と見なされます。
  * `level`:[in] 境界がテストされる含む四分木のレベル: 木全体の境界をテストしたい場合は 0 を指定します。
  * `faces`:[in,out] サイズ 4 の配列で、埋められます: faces[i] が真であれば、その範囲がその面に触れています。
  * `corners`:[in,out] サイズ 4 の配列で、埋められます: corners[i] が真であれば、その範囲がそのコーナーに触れています。**faces** または **corners** は NULL である可能性があります。

### 戻り値

**faces** と **corners** に同じ情報をエンコードした int32_t を返します: 最初の (最小の) 4 ビットは 4 つの面を表し、次の 4 ビットは 4 つのコーナーを表します。

### プロトタイプ

```c
int32_t p4est_find_range_boundaries (p4est_quadrant_t * lq, p4est_quadrant_t * uq, int level, int faces[], int corners[]);
```
