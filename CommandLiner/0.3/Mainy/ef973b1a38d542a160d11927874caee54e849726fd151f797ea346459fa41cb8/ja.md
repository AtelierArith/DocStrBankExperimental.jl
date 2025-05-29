```
@main, @mn
@ismain
@guard
```

メインガードヘルパー:

  * `@main`: スクリプトとして実行される場合、ユーザーが提供する `main` 関数を呼び出します。
  * `@mn`: 同様ですが、（ユーザー提供の）`mn` 関数を呼び出します（互換性のため、将来的にJuliaが `main` を処理する場合）。
  * `@ismain`: ブール値を返します; 使用法: `@ismain()  &&  myfunction()`。
  * `@guard`: 短縮形; 使用法: `@guard myfunction()`。

`@main` と `@mn` は、メインコールを `hushexit` でラップし、SIGPIPE と割り込みを処理します。

また、`hushexit` も参照してください。
