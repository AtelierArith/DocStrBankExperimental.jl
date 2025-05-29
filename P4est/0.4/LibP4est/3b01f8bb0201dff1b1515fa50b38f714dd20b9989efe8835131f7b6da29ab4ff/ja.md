```
sc_mstamp_truncate(mst)
```

スタンプ構造体内のすべてのメモリを解放し、新たに初期化します。これは、同じ stamp*unit と elem*size で sc*mstamp*reset を呼び出した後に sc*mstamp*init を呼び出すことに相当します。

### パラメータ

  * `Properly`:[in,out] 初期化されたスタンプコンテナ。出力時には、その要素が解放され、さらなる使用のために準備が整っています。

### プロトタイプ

```c
void sc_mstamp_truncate (sc_mstamp_t * mst);
```
