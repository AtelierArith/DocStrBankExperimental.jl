符号付き整数値をパックするためのコアフォーマット。

`negative fixint`、`positive fixint`、`signed 8`、`signed 16`、`signed 32`、`signed 64`のmsgpackフォーマットに基づいています。

## デフォルト

[`SignedFormat`](@ref) は、`Signed`のすべてのサブタイプのデフォルトフォーマットです。次のように使用します。

```
format(::Type{T}) = SignedFormat()
```

または

```
@pack T in SignedFormat
```

を使用して、タイプ `T` のデフォルトフォーマットを [`SignedFormat`](@ref) に設定します。`T` が抽象の場合は、すべてのサブタイプをカバーするために `{<: T}` を使用します。

## パッキング

[`SignedFormat`](@ref) におけるタイプ `T` の値をパックすることをサポートするには、次のように実装します。

```
destruct(val::T, ::SignedFormat)::Signed
```

## アンパッキング

[`SignedFormat`](@ref) にパックされたタイプ `T` の値をアンパックすることをサポートするには、次のように実装します。

```
construct(::Type{T}, ::Int64, ::SignedFormat)::T
```

または、コンストラクタ `T(::Int64)` が定義されていることを確認します。
