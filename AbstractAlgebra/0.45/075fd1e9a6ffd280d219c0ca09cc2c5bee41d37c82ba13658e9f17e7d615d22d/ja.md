```
fraction_field(R::Ring; cached::Bool=true)
```

与えられた基底環 $R$ の分数体の親オブジェクトを返します。`cached == true`（デフォルト）であれば、返される親オブジェクトはキャッシュされ、同じ基底環 $R$ が供給されたときにコンストラクタへの呼び出しによって常に返されます。
