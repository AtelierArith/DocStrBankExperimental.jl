```
energydiff(pb::Problem;T,rel)
```

与えられた時間 `T` と初期時間の間で解かれた初期値問題 `pb` のエネルギーの差を計算します。

キーワード引数 `T` はオプションで、デフォルトでは最後に計算された時間が使用されます。

キーワード引数 `rel=true`（デフォルトはfalse）の場合、初期値を基準として相対差を計算します。
