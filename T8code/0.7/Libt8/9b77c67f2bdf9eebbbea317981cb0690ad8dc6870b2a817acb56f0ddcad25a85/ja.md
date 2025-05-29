```
t8_eclass_is_valid(eclass)
```

クラスが有効なクラスであるかどうかを確認します。有効なクラスであれば非ゼロを返し、クラスが T8*ECLASS*INVALID と等しい場合はゼロを返します。

# 引数

  * `eclass`:[in] 確認する eclass。

# 戻り値

*eclass* が有効であれば非ゼロ、そうでなければゼロを返します。

### プロトタイプ

```c
int t8_eclass_is_valid (t8_eclass_t eclass);
```
