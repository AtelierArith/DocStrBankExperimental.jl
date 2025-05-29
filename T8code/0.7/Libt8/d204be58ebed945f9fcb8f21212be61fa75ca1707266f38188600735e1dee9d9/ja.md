```
t8_element_refines_irregular(ts)
```

ツリー内に、2^dim の子に細分化されない要素が1つでも存在する場合は true を返します。それ以外の場合は false を返します。

### プロトタイプ

```c
int t8_element_refines_irregular (const t8_eclass_scheme_c *ts);
```
