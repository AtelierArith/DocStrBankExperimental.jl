```
t8_geometry_zero_new()
```

新しいゼロジオメトリを作成します。ジオメトリはすべての木のタイプのみであり、木のタイプが持つ頂点の数だけあります。頂点はt8*cmesh*set*tree*vertices関数を介して保存されます。次元と名前を「t8*geom*zero_」に設定します。

# 戻り値

t8*geometry*zero () コンストラクタが呼び出されたかのように、割り当てられたt8*geometry*zero構造体へのポインタ。

### プロトタイプ

```c
t8_geometry_c * t8_geometry_zero_new ();
```
