```
p4est_quadrant_find_owner(p4est_, treeid, face, q)
```

四分木の所有者のプロセッサIDを取得します。四分木は、木の外側にある面（および面のみ）に位置することがあります。

!!! warning
    木のエッジやコーナーの隣接者には機能しません。


### パラメータ

  * `p4est`:[in] 四分木を検索する森林。
  * `treeid`:[in] 四分木が属する木。
  * `face`:[in] 知っている場合は面の方向を指定し、そうでない場合は-1を指定します。
  * `q`:[in] 検索対象の四分木。

### 戻り値

所有者のプロセッサID、または四分木がメッシュの外にある場合は-1。

### プロトタイプ

```c
int p4est_quadrant_find_owner (p4est_t * p4est, p4est_topidx_t treeid, int face, const p4est_quadrant_t * q);
```
