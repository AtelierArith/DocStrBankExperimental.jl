```
@config default_config my_function(x; a, b) = ...
```

このマクロは、変数 `a` と `b` にアクセスできる関数 `my_function(config, x)` を作成します。値 `a` と `b` は、`config` に存在する場合はそれらの値が使用され、存在しない場合は `default_config` の値が使用されます。
