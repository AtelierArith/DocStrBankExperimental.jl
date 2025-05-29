```
AbstractRuntimeOptions
```

シンボリック回帰アルゴリズムのランタイム構成パラメータを表す抽象型です。

`AbstractRuntimeOptions` は `equation_search` によって使用され、並列処理や反復制限などのランタイムの側面を制御します。`AbstractRuntimeOptions` をサブタイプ化することで、高度なユーザーは `equation_search` に渡すことでランタイムの動作をカスタマイズできます。

# 関連項目

  * [`RuntimeOptions`](@ref): `equation_search` で使用されるデフォルトの実装。
  * [`equation_search`](@ref SymbolicRegression.equation_search): シンボリック回帰を実行するためのメイン関数。
  * [`AbstractOptions`](@ref SymbolicRegression.CoreModule.OptionsStruct.AbstractOptions): オプションをカスタマイズするための抽象型の拡張方法を参照してください。
