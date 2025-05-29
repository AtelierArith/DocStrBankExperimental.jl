```
check_no_stale_explicit_imports(mod::Module, file=pathof(mod); ignore::Tuple=(), allow_unanalyzable::Tuple=())
```

`mod` またはそのサブモジュールのいずれにも古い（未使用の）明示的インポートがないことを確認し、もしあれば `StaleImportsException` をスローし、そうでなければ `nothing` を返します。

これはパッケージのテストで使用できます。例えば、

```julia
@test check_no_stale_explicit_imports(MyPackage) === nothing
```

## 一部のサブモジュールを解析不可にすることを許可する

`allow_unanalyzable` を解析不可とすることが許可されたサブモジュールのタプルとして渡します。解析不可と見なされる他のサブモジュールが見つかった場合、`UnanalyzableModuleException` がスローされます。

## 一部の古い明示的インポートを許可する

`ignore` が指定されている場合、それは古い明示的インポートとして許可される名前を表す `Symbol` のタプルであるべきです。例えば、

```julia
@test check_no_stale_explicit_imports(MyPackage; ignore=(:DataFrame,)) === nothing
```

は、名前 `DataFrame` の明示的インポートを除いて、古い明示的インポートがないことを確認します。
