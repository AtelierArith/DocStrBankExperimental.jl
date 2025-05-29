```
MLJModels.load(name; pkg=nothing, add=false, verbosity=0, mod=Main)
```

実験的なメソッド。現在はプライベートです。

指定されたモジュール `mod` に実行時にモデルコードをロードします。これは、呼び出しモジュールに呼び出し時にコードをロードする `@load` とは対照的です。
