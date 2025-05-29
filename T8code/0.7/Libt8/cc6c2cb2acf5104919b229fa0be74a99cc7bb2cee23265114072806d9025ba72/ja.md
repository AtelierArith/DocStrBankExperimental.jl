```
t8_refcount_new()
```

新しい参照カウンタを作成し、カウントを1に初期化します。新しく割り当てられた refcount*t に対して [`t8*refcount_init`](@ref) を呼び出すのと同等です。これは t8*refcount*destroy で解放することが必須です。

# 戻り値

カウントが1に設定された割り当てられた参照カウンタ。

### プロトタイプ

```c
t8_refcount_t * t8_refcount_new (void);
```
