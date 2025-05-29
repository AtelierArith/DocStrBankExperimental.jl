ブール値をパッキングするためのコアフォーマット。

msgpackフォーマット`boolean`に基づいています。

## デフォルト

[`BoolFormat`](@ref)は`Bool`のデフォルトフォーマットです。次のように使用します。

```
format(::Type{T}) = BoolFormat()
```

または

```
@pack T in BoolFormat
```

で、タイプ`T`のデフォルトフォーマットとして[`BoolFormat`](@ref)を設定します。`T`が抽象型の場合は、すべてのサブタイプをカバーするために`{<: T}`を使用します。

## パッキング

[`BoolFormat`](@ref)でタイプ`T`の値をパッキングすることをサポートするには、次のように実装します。

```
destruct(val::T, ::BoolFormat)::Bool
```

## アンパッキング

[`BoolFormat`](@ref)でパッキングされたタイプ`T`の値をアンパッキングすることをサポートするには、次のように実装します。

```
construct(::Type{T}, ::Bool, ::BoolFormat)::T
```

または、コンストラクタ`T(::Bool)`が定義されていることを確認します。
