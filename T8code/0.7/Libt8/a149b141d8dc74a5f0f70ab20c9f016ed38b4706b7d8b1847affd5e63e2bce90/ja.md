```
t8_scheme_cxx_ref(scheme)
```

スキームの参照カウンタを増やします。

# 引数

  * `scheme`:[in,out] 入力時、このスキームは生きている必要があります。つまり、正の参照カウントで存在している必要があります。

### プロトタイプ

```c
void t8_scheme_cxx_ref (t8_scheme_cxx_t *scheme);
```
