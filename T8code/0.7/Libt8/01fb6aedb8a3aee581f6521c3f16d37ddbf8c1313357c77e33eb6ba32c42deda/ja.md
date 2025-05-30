```
t8_geometry_linear_new()
```

新しい線形ジオメトリを作成します。ジオメトリはすべての木のタイプのみであり、木のタイプが持つ頂点の数だけの頂点があります。頂点は t8*cmesh*set*tree*vertices 関数を介して保存されます。次元と名前を "t8*geom*linear" に設定します。

# 戻り値

t8*geometry*linear () コンストラクタが呼び出されたかのように、割り当てられた t8*geometry*linear 構造体へのポインタ。

### プロトタイプ

```c
t8_geometry_c * t8_geometry_linear_new ();
```
