```
Tables.istable(x) => Bool
```

オブジェクトが特にテーブルであることを定義しているかどうかを確認します。すべての有効なテーブルがtrueを返すわけではないことに注意してください。なぜなら、`NamedTuple`の`Generator`が`NamedTuple`を反復処理し、`AbstractRow`インターフェースを満たすため、"実行時"にTables.jlインターフェースを満たすことが可能だからです。しかし、ジェネレーターがテーブルであることを静的に知る方法はありません。

`MyType`を実装するユーザーには、`istable(::Type{MyType})`のみを定義することをお勧めします。`istable(::MyType)`は自動的にこのメソッドに委譲されます。

`istable`はフォールバックとして`TableTraits.isiterabletable`を呼び出します。これは、いくつかのコンテキストでかなりの実行時オーバーヘッドを持つ可能性があります。これを避け、`istable`をコンパイル時のトレイトとして使用するには、`istable(typeof(obj))`のように型に対して呼び出すことができます。
