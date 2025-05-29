```
t8_element_array_init(element_array, scheme)
```

既に割り当てられた（または静的な）配列構造を初期化します。

# 引数

  * `element_array`:[in,out] 初期化される配列構造。
  * `scheme`:[in] 保存すべき要素のeclassスキーム。

### プロトタイプ

```c
void t8_element_array_init (t8_element_array_t *element_array, t8_eclass_scheme_c *scheme);
```
