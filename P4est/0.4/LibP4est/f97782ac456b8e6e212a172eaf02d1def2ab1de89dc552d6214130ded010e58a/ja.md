```
p8est_connectivity_new_shell()
```

球殻を構築する接続構造を作成します。これは、[-1,1]x[-1,1]x[1,2]の6つの接続された部分で構成されています。この接続は頂点を再利用し、幾何学的変換に依存しています。したがって、[`p8est_connectivity_complete`](@ref)には適していません。

### プロトタイプ

```c
p8est_connectivity_t *p8est_connectivity_new_shell (void);
```
