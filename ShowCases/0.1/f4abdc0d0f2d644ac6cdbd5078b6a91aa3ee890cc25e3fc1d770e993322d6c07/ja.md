```
ShowTypeOf(o, type_style=Style(), show_module=:context, show_params=true, kw...)
```

オブジェクト `o` の型を表示します。

## 引数

  * `type_style::Style`: 型に使用するスタイル。
  * `show_module::Symbol`: 型とそのパラメータのモジュールを表示するかどうか。オプションについては [`ShowType`](@ref) を参照してください。
  * `kw`: [`ShowParams`](@ref) に渡されるその他のキーワード引数。
