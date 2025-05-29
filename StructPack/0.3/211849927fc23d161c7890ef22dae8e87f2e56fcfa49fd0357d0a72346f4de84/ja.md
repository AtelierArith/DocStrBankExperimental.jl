バイナリ値をパッキングするためのコアフォーマット。

msgpackフォーマットの`bin 8`、`bin 16`、`bin 32`に基づいています。

## デフォルト

次のように使用します。

```
format(::Type{T}) = BinaryFormat()
```

または

```
@pack T in BinaryFormat
```

で、タイプ`T`のデフォルトフォーマットとして[`BinaryFormat`](@ref)を設定します。`T`が抽象型の場合は、すべてのサブタイプをカバーするために`{<: T}`を使用します。

## パッキング

[`BinaryFormat`](@ref)でタイプ`T`の値をパッキングすることをサポートするには、次のように実装します。

```
destruct(val::T, ::BinaryFormat)::R
```

返される値`ret::R`は、`sizeof(ret)`（バイト数）および`write(io, ret)`を実装する必要があります。

## アンパッキング

[`BinaryFormat`](@ref)でパッキングされたタイプ`T`の値をアンパッキングすることをサポートするには、次のように実装します。

```
construct(::Type{T}, ::Vector{UInt8}, ::BinaryFormat)::T
```

または、コンストラクタ`T(::Vector{UInt8})`が定義されていることを確認します。
