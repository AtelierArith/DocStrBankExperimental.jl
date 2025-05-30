```
t8_forest_set_adapt(forest, set_from, adapt_fn, recursive)
```

コミット時に適応関数を使用してソースフォレストを設定します。デフォルトでは、フォレストはソース **set_from** の所有権を取得し、t8*forest*commit を呼び出すと破棄されます。**set_from** の所有権を保持するには、この関数に渡す前に t8*forest*ref を呼び出してください。これは、**set_from** を使用し続けたり、参照解除したりすることが違法であることを意味します。この関数に渡す前に直接参照されている場合を除きます。

!!! note
    この設定は t8*forest*set*partition と t8*forest*set*balance と組み合わせることができます。これらの操作が実行される順序は常に 1) 適応 2) バランス 3) パーティション です。


!!! note
    この設定は t8*forest*set_copy と組み合わせることはできず、この設定を上書きします。


# 引数

  * `forest`:[in,out] フォレスト
  * `set_from`:[in] **forest** が適応されるソースフォレスト。所有権を取得します。**set_from** を参照することでこれを防ぐことができます。NULL の場合、以前（または後に）設定されたフォレストが取得されます (t8*forest*set*partition, t8*forest*set*balance)。
  * `adapt_fn`:[in] コミット時に使用される適応関数。
  * `recursive`:[in] 適応が再帰的に行われるかどうかを指定するフラグ。値がゼロの場合、適応は再帰的ではなく、それ以外の場合は再帰的です。

### プロトタイプ

```c
void t8_forest_set_adapt (t8_forest_t forest, const t8_forest_t set_from, t8_forest_adapt_t adapt_fn, int recursive);
```
