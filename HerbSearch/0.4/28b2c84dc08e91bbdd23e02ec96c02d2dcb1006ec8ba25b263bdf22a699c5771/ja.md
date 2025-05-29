```
@programiterator
```

プログラムイテレータを作成するための標準的な方法です。このマクロは、`ProgramIterator` ドキュメントにリストされている期待されるフィールドを自動的に宣言します。マクロが受け入れる構文は次のとおりです（角括弧で囲まれたものはオプションです）： `@programiterator [mutable] <IteratorName>(         <arg₁>,         ...,         <argₙ>     ) [<: <SupertypeIterator>]` マクロは、`SupertypeIterator` が `ProgramIterator` のサブタイプであることを確認するアサーションを発行します。そうでない場合、ArgumentError がスローされます。スーパタイプが指定されていない場合、新しいイテレータは `ProgramIterator` を直接拡張します。各 <argᵢ> は、構造体宣言で有効な（ほぼ）任意の式であり、カンマで区切る必要があります。既知の例外の1つは、内部コンストラクタは常に拡張された `function <name>(...) ... end` 構文を使用して指定する必要があることです。`mutable` キーワードは、宣言された構造体が可変かどうかを決定します。
