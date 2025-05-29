符号なし整数値をパッキングするためのコアフォーマット。

`positive fixint`、`unsigned 8`、`unsigned 16`、`unsigned 32`、`unsigned 64`のmsgpackフォーマットに基づいています。

## デフォルト

[`UnsignedFormat`](@ref) は、`Unsigned`のすべてのサブタイプのデフォルトフォーマットです。次のように使用します。

```
format(::Type{T}) = UnsignedFormat()
```

または

```
@pack T in UnsignedFormat
```

を使用して、[`UnsignedFormat`](@ref) を型 `T` のデフォルトフォーマットにします。`T` が抽象型の場合は、すべてのサブタイプをカバーするために `{<: T}` を使用します。

## パッキング

[`UnsignedFormat`](@ref) において型 `T` の値をパッキングすることをサポートするには、次のように実装します。

```
destruct(val::T, ::UnsignedFormat)::Unsigned
```

## アンパッキング

[`UnsignedFormat`](@ref) にパッキングされた型 `T` の値をアンパッキングすることをサポートするには、次のように実装します。

```
construct(::Type{T}, ::UInt64, ::UnsignedFormat)::T
```

または、コンストラクタ `T(::UInt64)` が定義されていることを確認します。
