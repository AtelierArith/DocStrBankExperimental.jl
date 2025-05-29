```
getblock(blockname::String; api::AbstractPrefectConfig = PrefectAPI())
```

指定されたURLエンドポイントに`HTTP.get()`呼び出しを行い、デフォルトのエンドポイントは`PrefectAPI`によって構築されます。Prefect Block仕様を含むDictを返します。
