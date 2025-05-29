```
as_return(T, f) -> g
TypeStableFunction{T}(f) -> g
TypeStableFunction(f, argtypes...) -> g
```

は、返される型 `T` が保証された呼び出し可能なオブジェクト `g` を生成します。あるいは、関数の引数の型 `argtypes...` を指定して返される型 `T` を推論することもできます。次の式が成り立ちます：

```
g(args...; kwds...) === as(T, f(args...; kwds...))
```

任意の引数 `args...` とキーワード `kwds...` に対してです。`Base.promote_op` メソッドの制限により、キーワードの型に基づいて `T` を推論することは現在不可能であることに注意してください。

メソッド [`return_type(g)`](@ref) と `parent(g)` を使用して、それぞれ `T` と `f` を取得できます。

`T` が指定されている場合、次のように類似のオブジェクトが与えられます：

```
g = as(T)∘f
```
