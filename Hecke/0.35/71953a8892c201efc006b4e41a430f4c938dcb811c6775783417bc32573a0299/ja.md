```
NonSimpleNumField{T}
```

すべての数体のための一般的で抽象的なオーバータイプで、（型によって）複数の生成元によって生成されます。 `T` は係数体の要素の型です。典型的な例は二次の二次体です：     QQ[sqrt 2, sqrt 3] これは単純な拡張に変換できます（マップを使用して）、例えば `absolute_simple_field` または `simple_extension` を参照してください。
