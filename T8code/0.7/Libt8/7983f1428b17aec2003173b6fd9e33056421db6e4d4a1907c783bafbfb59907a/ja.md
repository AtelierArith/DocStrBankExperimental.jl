```
t8_refcount_destroy(rc)
```

t8*refcount*newで割り当てた参照カウンタを破棄します。その参照カウントはゼロに減少している必要があります。

# 引数

  * `rc`:[in,out] 割り当てられた、以前は有効な参照カウンタ。

### プロトタイプ

```c
void t8_refcount_destroy (t8_refcount_t *rc);
```
