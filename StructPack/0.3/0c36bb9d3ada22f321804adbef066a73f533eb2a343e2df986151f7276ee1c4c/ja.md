バイナリ形式で配列をパックします。  

[`BinVectorFormat`](@ref) に基づいています。

## デフォルト

`BinArrayFormat` は `N > 1` の `BitArray{N}` のデフォルト形式です。次のように使用します。

```
format(::Type{T}) = BinArrayFormat()
```

または

```
@pack T in BinArrayFormat
```

で `T` のデフォルト形式を `BinVectorFormat` に設定します。`T` が抽象型の場合は、すべてのサブタイプをカバーするために `{<: T}` を使用します。

## パッキング

`BinArrayFormat` で型 `T` の値をパックすることをサポートするには、次のように実装します。

```
destruct(val::T, ::BinArrayFormat)::R
```

ここで、返される値 `ret::R` は `Base.size` を定義し、[`BinaryFormat`](@ref) でパック可能でなければなりません。

## アンパッキング

`BinArrayFormat` にパックされた型 `T` の値をアンパックすることをサポートするには、次のように実装します。

```
construct(::Type{T}, ::BinArrayValue{Vector{UInt8}}, ::BinArrayFormat)::T
```

または、コンストラクタ `T(val::BinArrayValue{Vector{UInt8}})` が定義されていることを確認します（[`BinArrayValue`(@ref)]を参照）。
