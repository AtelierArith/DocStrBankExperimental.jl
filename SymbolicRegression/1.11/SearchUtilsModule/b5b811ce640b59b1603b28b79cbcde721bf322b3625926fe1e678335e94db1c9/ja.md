```
AbstractSearchState{T,L,N}
```

シンボリック回帰中の検索プロセスの内部状態をカプセル化する抽象型です。

`AbstractSearchState` インスタンスは、`equation_search` によって内部的に使用される、集団や進捗メトリックなどの情報を保持します。`AbstractSearchState` をサブタイプ化することで、検索状態管理のカスタマイズが可能になります。

`equation_search` のソースを見て、これがどのように使用されているかを確認してください。

# 参照

  * [`SearchState`](@ref): `AbstractSearchState` のデフォルト実装。
  * [`equation_search`](@ref SymbolicRegression.equation_search): `AbstractSearchState` が利用される関数。
  * [`AbstractOptions`](@ref SymbolicRegression.CoreModule.OptionsStruct.AbstractOptions): オプションをカスタマイズするための抽象型の拡張方法を参照してください。
