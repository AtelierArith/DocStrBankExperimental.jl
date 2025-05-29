```
p8est_quadrant_find_owner(p8est_, treeid, face, q)
```

四分木の所有者のプロセッサIDを取得します。四分木は、ツリーの外側に面がある場合（面のみ）に存在する可能性があります。

!!! warning
    ツリーのエッジやコーナーの隣接者には機能しません。


### パラメータ

  * `p8est`:[in] 四分木を検索する森林。
  * `treeid`:[in] 四分木が属するツリー。
  * `face`:[in] 知っている場合は面の方向を指定し、そうでない場合は-1を指定します。
  * `q`:[in] 検索対象の四分木。

### 戻り値

所有者のプロセッサID、または四分木がメッシュの外にある場合は-1。

### プロトタイプ

```c
int p8est_quadrant_find_owner (p8est_t * p8est, p4est_topidx_t treeid, int face, const p8est_quadrant_t * q);
```
