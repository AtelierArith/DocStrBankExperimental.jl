```
t8_cmesh_trees_init(ptrees, num_procs, num_trees, num_ghosts)
```

ツリー構造を初期化し、その部分を割り当てます。この関数は、from*procs 配列を初期化せずに割り当て、tree*to*proc および ghost*to_proc 配列も割り当てます。ツリーやゴーストのためのメモリは割り当てられません。

# 引数

  * `[in,ou`: ptrees 初期化されるツリー構造。
  * `num_procs`:[in] from_proc 配列のエントリ数（プロセスごとに異なる場合があります）。
  * `num_trees`:[in] この構造に格納されるツリーの数。
  * `num_ghosts`:[in] この構造に格納されるゴーストの数。

### プロトタイプ

```c
void t8_cmesh_trees_init (t8_cmesh_trees_t *ptrees, int num_procs, t8_locidx_t num_trees, t8_locidx_t num_ghosts);
```
