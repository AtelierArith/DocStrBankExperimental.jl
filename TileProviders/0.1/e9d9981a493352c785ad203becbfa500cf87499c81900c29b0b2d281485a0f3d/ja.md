```
geturl(provider::Provider, x::Integer, y::Integer, z::Integer)
```

プロバイダーのURL内の `x`、`y`、`z` を置き換えます。

プロバイダーオプションに `:max_zoom` と `:attribution` 以外のキーがある場合、それらも置き換えられます。

私たちはLeaflet.jsの動作に従うため、彼らのプロバイダーURLは `Provider` で修正なしに機能します。
