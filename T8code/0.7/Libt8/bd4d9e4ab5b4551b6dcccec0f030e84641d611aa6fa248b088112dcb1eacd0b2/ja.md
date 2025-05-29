```
t8_forest_set_scheme(forest, scheme)
```

フォレストに関連付けられた要素スキームを設定します。デフォルトでは、フォレストはスキームの所有権を持ち、フォレストが破棄されるとスキームも破棄されます。スキームの所有権を保持するには、t8*scheme*refを呼び出してからt8*forest*set_schemeに渡します。これは、スキームをこの関数に渡す前に直接参照されていない限り、スキームを使用したり、参照解除したりすることが違法であることを意味します。

# 引数

  * `forest`:[in,out] スキーム変数が設定されるフォレスト。
  * `scheme`:[in] 設定されるスキーム。所有権を取得します。これは**scheme**を参照することで防ぐことができます。

### プロトタイプ

```c
void t8_forest_set_scheme (t8_forest_t forest, t8_scheme_cxx_t *scheme);
```
