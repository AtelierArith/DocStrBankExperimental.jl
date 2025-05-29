```
p6est_reset_data(p6est_, data_size, init_fn, user_pointer)
```

ユーザーポインタと要素データをリセットします。データサイズが変更されると、クアドラントデータは解放され、新たに割り当てられます。初期化コールバックは各クアドラントで呼び出されます。古いuser_dataの内容は無視されます。

### パラメータ

  * `data_size`:[in] 各クアドラントのデータサイズで、ゼロにすることもできます。その場合、user*data*poolはNULLに設定されます。
  * `init_fn`:[in] 自動的に割り当てられたuser_dataを初期化するためのコールバック関数です。
  * `user_pointer`:[in] init*fnが最初に呼び出される前に、`p6est`のuser*pointerメンバーに割り当てます。

### プロトタイプ

```c
void p6est_reset_data (p6est_t * p6est, size_t data_size, p6est_init_t init_fn, void *user_pointer);
```
