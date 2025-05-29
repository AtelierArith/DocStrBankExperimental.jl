```
check_no_implicit_imports(mod::Module, file=pathof(mod); skip=(mod, Base, Core), ignore::Tuple=(),
                          allow_unanalyzable::Tuple=())
```

`mod` またはそのサブモジュールが暗黙のインポートに依存していないことを確認し、そうであれば `ImplicitImportsException` をスローし、そうでなければ `nothing` を返します。

この関数はパッケージのテストで使用できます。例えば：

```julia
@test check_no_implicit_imports(MyPackage) === nothing
```

## 一部のサブモジュールを解析不能にすることを許可する

解析不能と見なされることが許可されるサブモジュールのタプルとして `allow_unanalyzable` を渡します。解析不能と見なされる他のサブモジュールが見つかった場合、`UnanalyzableModuleException` がスローされます。

これらの解析不能なサブモジュールは、代わりに `ignore` に含めることもできます。

## 一部の暗黙のインポートを許可する

`skip` キーワード引数を渡すことで、いくつかのモジュール（およびそのサブモジュール）からの暗黙のインポートを許可できます。デフォルトでは、`skip` は `(Base, Core)` に設定されています。例えば：

```julia
@test check_no_implicit_imports(MyPackage; skip=(Base, Core, DataFrames)) === nothing
```

は、Base、Core、および DataFrames 以外のモジュールからの暗黙のインポートがないことを確認します。

さらに、キーワード `ignore` を渡すことで、無視するアイテムのタプルを表すことができます。これらは次のようになります：

  * モジュール：`mod` のサブモジュールのうち、`ignore` の要素に一致するものはスキップされます。これを使用して、パッケージの一部のサブモジュールでの暗黙のインポートの使用を許可できます。
  * シンボル：`ignore` の要素に一致する名前の暗黙のインポートは無視されます（スローされません）。
  * `symbol => module` ペア：そのシンボルに一致する名前の暗黙のインポートが、そのモジュールに一致するモジュールからのものであれば無視されます。

これらの無視される要素のタイプを組み合わせることができます。例えば：

```julia
@test check_no_implicit_imports(MyPackage; ignore=(:DataFrame => DataFrames, :ByRow, MySubModule)) === nothing
```

これは次のことを行います：

1. DataFrames からの `DataFrame` の暗黙のインポートを無視します。
2. どのモジュールからの名前 `ByRow` の暗黙のインポートも無視します。
3. `MyPackage` のサブモジュール `MySubModule` に存在する暗黙のインポートを無視します。

しかし、他の暗黙のインポートがないことを確認します。
