バイナリ形式でベクトルをパックします。  

[`BinaryFormat`](@ref)に基づいています。

## デフォルト

`BinVectorFormat`は`BitVector`のデフォルト形式です。次のように使用します。

```
format(::Type{T}) = BinVectorFormat()
```

または

```
@pack T in BinVectorFormat
```

を使用して、`T`のデフォルト形式を`BinVectorFormat`にします。`T`が抽象型の場合は、すべてのサブタイプをカバーするために`{<: T}`を使用します。

## パッキング

`BinVectorFormat`で型`T`の値をパックすることをサポートするには、次のように実装します。

```
destruct(val::T, ::BinVectorFormat)::R
```

返される値`ret::R`は、[`BinaryFormat`](@ref)でパック可能でなければなりません。

## アンパッキング

`BinVectorFormat`でパックされた型`T`の値をアンパックすることをサポートするには、次のように実装します。

```
construct(::Type{T}, ::Vector{UInt8}, ::BinVectorFormat)::T
```

または、コンストラクタ`T(bytes::Vector{UInt8})`が定義されていることを確認します。
