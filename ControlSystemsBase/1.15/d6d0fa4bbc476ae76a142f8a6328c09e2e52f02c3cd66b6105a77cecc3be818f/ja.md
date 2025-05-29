```
feedback(sys)
feedback(sys1, sys2)
```

一般的なLTIシステムに対して、`feedback`は負のフィードバック相互接続を形成します

```julia
>-+ sys1 +-->
  |      |
 (-)sys2 +
```

第二のシステムが指定されていない場合、負の単位フィードバックが仮定されます
