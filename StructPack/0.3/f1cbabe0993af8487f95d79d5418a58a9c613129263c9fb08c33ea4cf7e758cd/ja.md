文字列値をパッキングするためのコアフォーマット。

`fixstr`、`str 8`、`str 16`、`str 32`のmsgpackフォーマットに基づいています。

## デフォルト

[`StringFormat`](@ref)は、`Symbol`およびすべての`AbstractString`のサブタイプのデフォルトフォーマットです。次のように使用します。

```
format(:: Type{T}) = StringFormat()
```

または

```
@pack T in StringFormat
```

で、[`StringFormat`](@ref)を型`T`のデフォルトフォーマットにします。`T`が抽象型の場合は、すべてのサブタイプをカバーするために`{<: T}`を使用します。

## パッキング

[`StringFormat`](@ref)で型`T`の値をパッキングすることをサポートするには、次のように実装します。

```
destruct(val::T, ::StringFormat)::R
```

返される値`ret::R`は、`sizeof(ret)`（バイト数）および`write(io, ret)`を実装する必要があります。

## アンパッキング

[`StringFormat`](@ref)でパッキングされた型`T`の値をアンパッキングすることをサポートするには、次のように実装します。

```
construct(:: Type{T}, ::String, ::StringFormat)::T
```

または、`convert(T, ::String)`が定義されていることを確認します。
