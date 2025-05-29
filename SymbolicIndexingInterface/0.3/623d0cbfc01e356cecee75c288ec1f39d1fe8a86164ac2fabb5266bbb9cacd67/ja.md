```
symbolic_container(indp)
```

`indp`を使用して、インデックスプロバイダーインターフェースを実装するオブジェクトを返します。`indp`自体がインターフェースを実装している場合、`indp`はそのまま返すことができます。すべてのインデックスプロバイダーインターフェースメソッドは、`symbolic_container(indp)`の同じメソッドを呼び出すことにフォールバックするため、他のオブジェクトへのすべての呼び出しを転送するインターフェースの単純な実装に使用できます。

このメソッドはオプションであることに注意してください。したがって、フォールバックを確認する正しい方法は次のとおりです。

```julia
hasmethod(symbolic_container, Tuple{typeof(indp)}) && symbolic_container(indp) != indp
```
