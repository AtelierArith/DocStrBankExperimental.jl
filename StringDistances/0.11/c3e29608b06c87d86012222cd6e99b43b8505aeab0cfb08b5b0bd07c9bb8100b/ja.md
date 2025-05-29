```
JaroWinkler(;p = 0.1, threshold = 0.3, maxlength = 4)
```

JaroWinkler距離を作成します

JaroWinkler距離は、Jaro距離として定義され、共通の接頭辞の長さを示す`l`が`maxlength`より小さい場合、$ (1-min(l,  maxlength) * p):で乗算され、`threshold`より低い場合に適用されます。
