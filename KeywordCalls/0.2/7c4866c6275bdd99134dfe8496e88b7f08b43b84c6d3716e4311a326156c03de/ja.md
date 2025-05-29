```
@kwstruct Foo(b,a,c)
```

`@kwcall Foo(b,a,c)` に加えて定義を行います

```
Foo(nt::NamedTuple{(:b, :a, :c), T}) where {T} = Foo{(:b, :a, :c), T}(nt)
```

これは、次の形式の `Foo` 構造体の存在を前提としています

```
Foo{N,T} [<: SomeAbstractTypeIfYouLike]
    someFieldName :: NamedTuple{N,T}
end
```

注意: デフォルト値（`@kwcall` のように）は現在 `@kwstruct` では機能しません。REPL では機能する可能性がありますが、これはワールドエイジの問題によるもののようです。この機能は将来のリリースで再びサポートされるかもしれません。
