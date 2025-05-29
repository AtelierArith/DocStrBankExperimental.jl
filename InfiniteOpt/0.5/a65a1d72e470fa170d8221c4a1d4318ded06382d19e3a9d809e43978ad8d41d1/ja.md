```
Infinite{VT <: VectorTuple} <: InfOptVariableType
```

無限変数を作成するための`DataType`です。これは、無限変数を作成するために`@variable`に追加の引数として渡すことができます：

```julia
@variable(model, var_expr, Infinite(parameter_refs...), args..., kwargs...)
```

ここで`parameter_refs`は、単一のパラメータ参照、同じマクロ呼び出しで定義されたパラメータを持つ単一のパラメータ配列、またはリストされた最初の2つのオプションのいずれかである複数の引数のいずれかです。

**フィールド**

  * `parameter_refs::VT`: 変数が依存する無限パラメータ。
