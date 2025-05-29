```
sc_mstamp_alloc(mst)
```

新しいアイテムを返します。返されたメモリは、コンテナが破棄されるか切り詰められるまで有効です。

### パラメータ

  * `Properly`:[in,out] 初期化されたスタンプコンテナ。

### 戻り値

使用する準備が整ったアイテムへのポインタ。mstに対してsc*stamp*destroyまたはsc*stamp*truncateが呼び出されるまで有効です。

### プロトタイプ

```c
void *sc_mstamp_alloc (sc_mstamp_t * mst);
```
