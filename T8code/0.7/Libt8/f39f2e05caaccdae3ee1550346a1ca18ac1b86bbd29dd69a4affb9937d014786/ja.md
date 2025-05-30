```
t8_forest_ghost_destroy(pghost)
```

ゴースト構造体が残りの参照が1つだけであることを確認し、それを破棄します。この関数は、最後の参照が削除されることがわかっている場合に、t8*ghost*unrefよりも好まれます。

# 引数

  * `pghost`:[in,out] このゴースト構造体は参照カウントが1でなければなりません。任意の状態（コミット済みまたは未コミット）である可能性があります。その後、実際にt8*forest*ghost_unrefを呼び出します。

### プロトタイプ

```c
void t8_forest_ghost_destroy (t8_forest_ghost_t *pghost);
```
