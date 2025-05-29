配列サイズを記憶する配列のフォーマット。

[`VectorFormat`](@ref) に基づいています。

## デフォルト

`ArrayFormat` は `AbstractArray` のデフォルトフォーマットです。次のように使用します。

```
format(::Type{T}) = ArrayFormat()
```

または

```
@pack T in ArrayFormat
```

で、`T` のデフォルトフォーマットを `ArrayFormat` に設定します。`T` が抽象型の場合は、すべてのサブタイプをカバーするために `{<: T}` を使用します。

## パッキング

`ArrayFormat` に型 `T` の値をパッキングすることをサポートするには、次のように実装します。

```
destruct(val::T, ::ArrayFormat)::R
```

ここで、返される値 `ret::R` は `size` を定義し、[`VectorFormat`](@ref) にパック可能でなければなりません。

## アンパッキング

`ArrayFormat` にパックされた型 `T` の値をアンパックすることをサポートするには、次のように実装します。

```
construct(::Type{T}, ::ArrayValue{Generator{T}}, ::ArrayFormat)::T
```

または、コンストラクタ `T(val::ArrayValue{Generator{T}})` が定義されていることを確認します（[`ArrayValue`](@ref) と [`Generator`](@ref) を参照）。
