Core format for packing nil values.

Built upon the msgpack format `nil`.

## Defaults

[`NilFormat`](@ref) は `Nothing` のデフォルトフォーマットです。次のように使用します。

```
format(::Type{T}) = NilFormat()
```

または

```
@pack T in NilFormat
```

で、[`NilFormat`](@ref) を型 `T` のデフォルトフォーマットにします。`T` が抽象型の場合は、すべてのサブタイプをカバーするために `{<: T}` を使用します。

## Packing

すべての型は [`NilFormat`](@ref) にパックできます。

## Unpacking

[`NilFormat`](@ref) にパックされた型 `T` の値をアンパックするには、次のように実装します。

```
construct(::Type{T}, ::Nothing, ::NilFormat)::T
```

または、コンストラクタ `T()` が定義されていることを確認してください。
