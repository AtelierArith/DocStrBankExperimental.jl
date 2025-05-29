```
t8_cmesh_trees_print(cmesh, trees)
```

木、ゴースト、およびその隣接点をASCII形式で標準出力に印刷します。この関数はデバッグ目的で使用されます。

# 引数

  * `cmesh`:[in] コミットされなければならない粗いメッシュ構造。
  * `trees`:[in] *cmesh* の木構造。

### プロトタイプ

```c
void t8_cmesh_trees_print (t8_cmesh_t cmesh, t8_cmesh_trees_t trees);
```
