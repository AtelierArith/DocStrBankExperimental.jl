msgpack拡張標準をサポートするためのフォーマット。

msgpackフォーマットの`fixext 1-8`および`ext 8-32`に基づいています。

## デフォルト

次のように使用します。

```
format(::Type{T}) = ExtensionFormat{I}()
```

または 

```
@pack T in ExtensionFormat{I}
```

これにより、msgpack拡張タイプ`I::Int8`を持つ[`ExtensionFormat`](@ref)が型`T`のデフォルトフォーマットになります。`T`が抽象型の場合は、すべてのサブタイプをカバーするために`{<: T}`を使用します。

## パッキング

[`ExtensionFormat`](@ref)で型`T`の値をパッキングすることをサポートするには、次のように実装します。

```
destruct(val::T, ::ExtensionFormat{I})::R
```

ここで、戻り値`ret::R`は`sizeof(ret)`（バイト数）および`write(io, ret)`を実装する必要があります。

## アンパッキング

[`ExtensionFormat`](@ref)でパッキングされた型`T`の値をアンパッキングすることをサポートするには、次のように実装します。

```
construct(::Type{T}, ::Vector{UInt8}, ::ExtensionFormat{I})::T
```

または、コンストラクタ`T(::Vector{UInt8})`が定義されていることを確認します。
