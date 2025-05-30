```
t8_forest_set_copy(forest, from)
```

コミット時にコピー元としてフォレストを設定します。デフォルトでは、フォレストはソース **from** の所有権を取得し、t8*forest*commit を呼び出すと破棄されます。**from** の所有権を保持するには、この関数に渡す前に t8*forest*ref を呼び出してください。これは、**from** をこの関数に渡す前に直接参照しない限り、**from** を使用したり、逆参照したりすることが違法であることを意味します。

!!! note
    この設定は t8*forest*set*adapt、t8*forest*set*partition、または t8*forest*set_balance と組み合わせることはできず、これらの設定を上書きします。


# 引数

  * `forest`:[in,out] フォレスト。
  * `from`:[in] t8*forest*commit で *forest* がコピーされる第二のフォレスト。

### プロトタイプ

```c
void t8_forest_set_copy (t8_forest_t forest, const t8_forest_t from);
```
