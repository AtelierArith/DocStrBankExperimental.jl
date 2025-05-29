```
sc_mstamp_reset(mst)
```

スタンプ構造体内のすべてのメモリと、以前に返されたすべてのアイテムを解放します。

### パラメータ

  * `Properly`:[in,out] 初期化されたスタンプコンテナ。出力時に、構造体は未定義です。

### プロトタイプ

```c
void sc_mstamp_reset (sc_mstamp_t * mst);
```
