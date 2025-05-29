```
sc_finalize()
```

すべてのパッケージの登録を解除し、メモリチェックを実行し、シグナルハンドラを削除し、sc*identifierおよびsc*root**をリセットします。この関数は、一貫性のないものが見つかった場合に中止しますが、グローバル変数default*abort*mismatchがfalseの場合は除きます。この関数はオプションです。この関数は、最初に[`sc*init`](@ref)を呼び出す必要はありません。

### プロトタイプ

```c
void sc_finalize (void);
```
