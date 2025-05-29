コアフォーマットはベクタ値をパッキングするためのものです。

`fixarray`、`array 16`、`array 32`のmsgpackフォーマットに基づいています。

## デフォルト

[`VectorFormat`](@ref)は、`Tuple`および`AbstractVector`のサブタイプのデフォルトフォーマットです。次のように使用します。

```
format(::Type{T}) = VectorFormat()
```

または

```
@pack T in VectorFormat
```

これにより、[`VectorFormat`](@ref)が型`T`のデフォルトフォーマットになります。`T`が抽象型の場合は、すべてのサブタイプをカバーするために`{<: T}`を使用します。

## パッキング

[`VectorFormat`](@ref)で型`T`の値をパッキングすることをサポートするには、次のように実装します。

```
destruct(val::T, ::VectorFormat)::R
```

返される値`ret::R`は、`Base.length(ret)`（エントリの数）を実装し、反復可能でなければなりません。`val`のエントリのフォーマットは、`state`が線形インデックスである[`valueformat`](@ref)を介して決定されます。

## アンパッキング

[`VectorFormat`](@ref)でパッキングされた型`T`の値をアンパッキングすることをサポートするには、次のように実装します。

```
construct(::Type{T}, values::Generator{T}, ::VectorFormat)::T
```

または、コンストラクタ`T(values::Generator{T})`が定義されていることを確認します（[`Generator`](@ref）を参照）。`values`のエントリのそれぞれの型とフォーマットは、`state`が線形インデックスである[`valuetype`](@ref)および[`valueformat`](@ref)を介して決定されます。

!!! 警告     構築中は、ジェネレーター`values`のすべてのエントリを反復処理する必要があります。`Generator{T}`は、アンパックされるIOソースから読み取る遅延マップをラップしているため、次のオブジェクトが処理される前に反復を行わないと、後続の値のアンパッキングに干渉します。同じ理由から、オブジェクト`values`を保存し、後でアクセスするべきではありません。
