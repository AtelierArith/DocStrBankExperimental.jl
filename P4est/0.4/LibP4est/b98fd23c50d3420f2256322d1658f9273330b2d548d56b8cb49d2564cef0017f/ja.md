```
p4est_ghost_is_valid(p4est_, ghost)
```

ゴースト構造が有効かどうかを確認します。ゴースト構造内で配列 ghosts が p4est*quadrant*compare*piggy 順にあるかどうかをテストします。ghost の各ランク内で、ghosts および mirrors の四分木の piggy3 データメンバー内の local*num が昇順であるかどうかをテストします。

[`p4est_locidx_t`](@ref) 配列が昇順であるかどうかをテストします（mirror*proc*mirrors は各ランク内で昇順）。

### パラメータ

  * `p4est`:[in] 森。
  * `ghost`:[in] ゴーストレイヤー構造。

### 戻り値

*ghost* が有効な場合は true を返します。

### プロトタイプ

```c
int p4est_ghost_is_valid (p4est_t * p4est, p4est_ghost_t * ghost);
```
