```
TypeUtils.Unsupported(T::DataType...)
```

は、型 `T...` のユニオンと型 `Unsupported` を生成します。このようなユニオンは、サポートされていない引数の型をマークするために使用でき、かつその型に適用可能なメソッド（おそらく指示的なエラーをスローするメソッド）を定義することができ、後で同じシグネチャで `Unsupported(T...)` を `T...` に置き換えることで拡張することができます。このトリックは、パッケージ拡張による事前コンパイルを妨げる競合を回避します。

例えば、メインパッケージでは：

```julia
some_method(some_arg::Unsupported{SomeType}) =
    error("package `SomeOtherPackage` has not yet been loaded")
```

そして拡張（例：`SomeOtherPackage` を使用する際に自動的にロードされる）では：

```julia
some_method(some_arg::SomeType) = do_something_with(some_arg)
```
