```
build_variable(
    _error::Function,
    info::VariableInfo,
    args...;
    kwargs...,
)
```

新しい [`AbstractVariable`](@ref) オブジェクトを返します。

このメソッドは、JuMP 拡張を作成する開発者によってのみ実装されるべきです。JuMP のユーザーによって呼び出されるべきではありません。

## 引数

  * `_error`: `error` の代わりに呼び出す関数。`_error` は、ユーザーに追加情報を付加したエラーメッセージを注釈します。
  * `info`: [`VariableInfo`](@ref) のインスタンス。これは、`info.lower_bound` や `info.binary` など、変数に関連するさまざまなフィールドを持っています。
  * `args`: [`@variable`](@ref) マクロを拡張するための追加の位置引数（オプション）。
  * `kwargs`: [`@variable`](@ref) マクロを拡張するためのキーワード引数（オプション）。

参照: [`@variable`](@ref)

!!! warning
    拡張は、異なるメソッドに呼び出しをディスパッチするために ONE の位置引数を持つメソッドを定義するべきです。ユーザーが引数を間違った順序で渡すと、複数の位置引数に依存する拡張は `MethodError` を引き起こします。


## 例

```julia
@variable(model, x, Foo)
```

は次のように呼び出されます

```julia
build_variable(_error::Function, info::VariableInfo, ::Type{Foo})
```

`Bin`、`Int`、`PSD` のような特別な位置引数を渡すことは問題ありません。キーワード引数も同様です：

```julia
@variable(model, x, Int, Foo(), mykwarg = true)
# または
@variable(model, x, Foo(), Int, mykwarg = true)
```

は次のように呼び出されます

```julia
build_variable(_error::Function, info::VariableInfo, ::Foo; mykwarg)
```

そして `info.integer` は true になります。

位置引数の順序は重要ではないことに注意してください。
