```
code(block::AbstractString; mod=Main, hide_module=false)
```

モジュール `mod` で評価される必要があるコード `block` を定義します。デフォルトでは、コードが評価されるモジュールはコードブロックの上に表示されます。これは `hide_module` を使用して無効にすることができます。
