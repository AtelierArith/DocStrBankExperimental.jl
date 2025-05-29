```
t8_element_is_root_boundary(ts, elem, face)
```

与えられた要素がそのルートツリーと特定の面を共有しているかどうかを計算します。

# 引数

  * `ts`:[in] クラススキームの実装。
  * `elem`:[in] 入力要素。
  * `face`:[in] *elem* の面。

# 戻り値

*face* が要素のルート要素のサブフェイスである場合は真。

### プロトタイプ

```c
int t8_element_is_root_boundary (const t8_eclass_scheme_c *ts, const t8_element_t *elem, int face);
```
