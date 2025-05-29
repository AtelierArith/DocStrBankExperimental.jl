```
p8est_connectivity_new_sphere()
```

固体球を構築する接続構造を作成します。これは2層と中央の立方体で構成されています。この接続は頂点を再利用し、幾何学的変換に依存しています。したがって、[`p8est_connectivity_complete`](@ref)には適していません。

### プロトタイプ

```c
p8est_connectivity_t *p8est_connectivity_new_sphere (void);
```
