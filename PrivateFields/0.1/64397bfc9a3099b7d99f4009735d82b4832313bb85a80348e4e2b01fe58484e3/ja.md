```
@private_method ...
```

このマクロの後に続くメソッドに、注釈付きの型に対して特定のフィールドへの特権アクセスがあることをタグ付けします。これにより、エラーを投げるのではなく、従来のドット構文 `a.b` を通じて型と対話することができます。

注意すべきは、`a.b` が `PrivateFields.getproperty_direct(a, :b)` に置き換えられるため、プロパティやフィールドの取得はそこで処理されるべきです。

# 使用法

特権アクセスを持たせたいメソッドシグネチャの引数に四つのコロンを付けて注釈します: `::::`

以下の例での `f` の定義を参照してください。

# 例

```@example
@private_struct struct Foo{X,Y}
    @private x::X
    y::Y
end

@private_method f(a::::Foo, b::Foo) = a.x + b.y

foo = Foo(1.0, 2.0)

@assert f(foo, foo) == 3.0

foo.x + foo.y # エラーを投げる
```
