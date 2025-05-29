```
compose(args...)
```

`args...`の合成関数を作成します。

`compose(f1, f2)(x)`は`f2(f1(x))`に等しいです。
