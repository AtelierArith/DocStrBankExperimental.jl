構造体のパッキング形式。

`fixmap`、`map 16`、`map 32`のmsgpack形式に基づいています。

## デフォルト

[`StructFormat`](@ref)は、どのタイプのデフォルトとしても使用されません。ただし、カスタム構造体をパックしたい場合は、最初の候補として使用するべきです。次のように使用します。

```
format(::Type{T}) = StructFormat()
```

または

```
@pack T in StructFormat
```

で、[`StructFormat`](@ref)を型`T`のデフォルト形式にします。`T`が抽象型の場合は、すべてのサブタイプをカバーするために`{<: T}`を使用します。

## パッキング

[`StructFormat`](@ref)で型`T`の値をパックすることをサポートするには、次のように実装します。

```
destruct(val::T, ::MapFormat)::R
```

ここで、返される値`ret::R`は`Base.length(ret)`（エントリの数）を実装し、エントリとしてキーと値のペアを持つことができる必要があります。

[`MapFormat`](@ref)とは対照的に、キーは常に[`StringFormat`](@ref)に格納され、値の形式は[`fieldformats`](@ref)を介して決定されます。これは、構造体の値エントリの形式のタプルを返す必要があります。

## アンパッキング

[`StructFormat`](@ref)でパックされた型`T`の値をアンパックすることをサポートするには、次のように実装します。

```
construct(::Type{T}, pairs::Generator{T}, ::StructFormat)::T
```

または、`T(values...)`というコンストラクタが定義されていることを確認します。ここで、`values`は`pairs`の値エントリを含みます。

値のそれぞれの型と形式は、[`fieldtypes`](@ref)と[`fieldformats`](@ref)を介してアンパッキング中に決定され、型と形式のタプルを返す必要があります。さらに、[`fieldnames`](@ref)が照会され、アンパッキング中に遭遇したキーが`T`と一致していることを確認します。

!!! note "StructFormat vs. MapFormat"
    [`StructFormat`](@ref)と[`MapFormat`](@ref)の両方を使用してカスタム構造体をパックできます。パフォーマンスは同等です。

      * [`MapFormat`](@ref)はより柔軟で、シンボルでないキーを処理できます。それに対して、[`StructFormat`](@ref)は静的なフィールド型、フィールド名、およびフィールド形式の情報を必要とします。
      * ただし、[`MapFormat`](@ref)はアンパッキング中にキーの値を再確認しないため、外部のmsgpackバイナリに適用するとデータが破損する可能性があります。

