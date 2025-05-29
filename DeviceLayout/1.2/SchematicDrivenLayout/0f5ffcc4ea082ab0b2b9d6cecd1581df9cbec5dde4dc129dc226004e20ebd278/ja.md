```
flatten(g::SchematicGraph; depth=-1)
```

`g`のコピーを作成し、すべての`AbstractCompositeComponent`をそのグラフに置き換えます。

非コンポジットコンポーネントの場合、同一の`ComponentNode`は保持されます。

# キーワード

  * `depth`: トップレベルの`AbstractCompositeComponent`を何回反復的にフラット化するか。負の値の場合、`AbstractCompositeComponent`が残らなくなるまで繰り返します。
