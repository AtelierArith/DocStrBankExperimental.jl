```
t8_refcount_init(rc)
```

参照カウンタを1に初期化します。この呼び出しの前の状態が未定義であっても合法です。

# 引数

  * `rc`:[out] この呼び出しによって参照カウンタが1に設定されます。

### プロトタイプ

```c
void t8_refcount_init (t8_refcount_t *rc);
```
