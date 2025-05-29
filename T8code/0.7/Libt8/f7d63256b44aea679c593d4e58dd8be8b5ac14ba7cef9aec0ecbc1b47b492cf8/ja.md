```
t8_forest_commit(forest)
```

森林にプロパティを割り当てて追加した後、変更をコミットします。この呼び出しは森林の内部状態を設定します。

# 引数

  * `forest`:[in,out] 最初に t8*forest*init で作成され、t8*forest*set_* 呼び出しで特化されている必要があります。

### プロトタイプ

```c
void t8_forest_commit (t8_forest_t forest);
```
