```
t8_geometry_lagrange_new()
```

指定された次元の新しいラグランジュ幾何を作成します。この幾何はすべてのツリータイプと互換性があり、マッピングに使用されるラグランジュ基底関数の数と同じ数の頂点を使用します。頂点はt8*cmesh*set*tree*vertices関数を介して保存されます。名前は「t8*geom*lagrange」に設定されます。

# 戻り値

t8*geometry*lagrange () コンストラクタが呼び出されたかのように、割り当てられたt8*geometry*lagrange構造体へのポインタ。

### プロトタイプ

```c
t8_geometry_c * t8_geometry_lagrange_new ();
```
