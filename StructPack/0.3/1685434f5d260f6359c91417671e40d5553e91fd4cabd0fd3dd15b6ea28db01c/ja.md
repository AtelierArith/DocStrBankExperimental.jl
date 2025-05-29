浮動小数点値をパッキングするためのコアフォーマット。

`float 32`、`float 64`のmsgpackフォーマットに基づいています。

## デフォルト

[`FloatFormat`](@ref)は、`Float16`、`Float32`、および`Float64`のデフォルトフォーマットです。次のように使用します。

```
format(::Type{T}) = FloatFormat()
```

または

```
@pack T in FloatFormat
```

で、[`FloatFormat`](@ref)を型`T`のデフォルトフォーマットにします。`T`が抽象型の場合は、すべてのサブタイプをカバーするために`{<: T}`を使用します。

## パッキング

[`FloatFormat`](@ref)で型`T`の値をパッキングすることをサポートするには、次のように実装します。

```
destruct(val::T, ::FloatFormat)::Union{Float16, Float32, Float64}
```

## アンパッキング

[`FloatFormat`](@ref)でパッキングされた型`T`の値をアンパッキングすることをサポートするには、次のように実装します。

```
construct(::Type{T}, ::Float64, ::FloatFormat)::T
```

または、コンストラクタ`T(::Float64)`が定義されていることを確認します。
