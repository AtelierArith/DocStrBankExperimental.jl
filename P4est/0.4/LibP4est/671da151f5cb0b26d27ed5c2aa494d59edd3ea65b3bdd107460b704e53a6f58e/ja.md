```
p8est_connectivity_new_torus(nSegments)
```

回転トーラスを構築する接続構造を作成します。

この接続は頂点を再利用し、幾何学的変換に依存しています。したがって、[`p8est_connectivity_complete`](@ref)には適していません。

この接続はdisk2d接続のアイデアを再利用しています。より正確には、トーラスは回転軸の周りにセグメントに分割され、各セグメントは5つの木（disk2dのように）で構成されています。木の総数はセグメントの数の5倍です。

この接続はp8est*geometry*new_torusと一緒に使用することを意図しています。

### パラメータ

  * `nSegments`:[in] 大円に沿った木の数

### プロトタイプ

```c
p8est_connectivity_t *p8est_connectivity_new_torus (int nSegments);
```
