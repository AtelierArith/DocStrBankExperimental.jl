```
UnitCatalogue
```

[`UnitFactorElement`](@ref) オブジェクトのコレクションです。これには、[`UnitPrefix`](@ref) タイプの単位接頭辞と、[`BaseUnit`](@ref) タイプの名前付き単位が含まれます。

単一の `UnitCatalogue` オブジェクトは、単位要素の一貫したライブラリとして機能します。ユーザーは、単位カタログに保存された接頭辞と単位定義に基づいて複合単位を構築できます。ほとんどの使用ケースでは、`UnitCatalogue()` を使用して単一の単位カタログを初期化するだけで十分です。返されるカタログには、国際単位系で使用が承認された単位接頭辞と名前付き単位が含まれています。

単位カタログに保存された単位接頭辞と基本単位は、[`Base.getproperty`](@ref) を使用して `name` フィールドを介してドット表記でアクセスできます。その結果、単位カタログに保存された要素の名前は一意である必要があります。

# フィールド

`UnitCatalogue` のフィールドは公開インターフェースの一部とは見なされず、ドット表記を使用してアクセスすることはできません。保存された [`UnitFactorElement`](@ref) オブジェクトには、以下のメソッドを介してアクセスできます。

  * [`Base.getproperty(unitCatalogue::UnitCatalogue, symbol::Symbol)`](@ref)
  * [`listUnitPrefixes(unitCatalogue::UnitCatalogue)`](@ref)
  * [`listBaseUnits(unitCatalogue::UnitCatalogue)`](@ref)
  * [`listUnitPrefixNames(unitCatalogue::UnitCatalogue)`](@ref)
  * [`listBaseUnitNames(unitCatalogue::UnitCatalogue)`](@ref)
  * [`providesUnitPrefix(unitCatalogue::UnitCatalogue, symbol::String)`](@ref)
  * [`providesBaseUnit(unitCatalogue::UnitCatalogue, symbol::String)`](@ref)
  * [`add!(unitCatalogue::UnitCatalogue, unitPrefix::UnitPrefix)`](@ref)
  * [`add!(unitCatalogue::UnitCatalogue, baseUnit::BaseUnit)`](@ref)
  * [`remove!(unitCatalogue::UnitCatalogue, elementName::String)`](@ref)

# コンストラクタ

```
UnitCatalogue(unitPrefixes::Vector{UnitPrefix}, baseUnits::Vector{BaseUnit})
UnitCatalogue(unitPrefixes::Vector, baseUnits::Vector)
UnitCatalogue()
```

# 例外を発生させる

  * `Alicorn.Exceptions.DuplicationError`: 同一の `name` フィールドを持つ [`UnitFactorElement`](@ref) オブジェクトを `UnitCatalogue` に追加しようとした場合

# 備考

[`UnitPrefix`](@ref) および [`BaseUnit`](@ref) 以外の型のベクターが提供された場合、コンストラクタはそれらをこれらの型に変換しようとします。

引数なしでコンストラクタが呼び出された場合、単位カタログにデフォルトの単位接頭辞と基本単位の定義が追加されます。

# 例

1. デフォルトの単位カタログを初期化し（国際単位系で使用が承認された標準単位接頭辞と名前付き単位を含む）、単位 $\mathrm{nm}$（ナノメートル）を定義するために使用します：

    ```jldoctest  julia> ucat = UnitCatalogue()  UnitCatalogue providing   21 unit prefixes   43 base units

    julia> nm = ucat.nano * ucat.meter  UnitFactor nm  ```
2. 空の単位カタログを初期化し（カスタム接頭辞と単位定義で満たすため）、名前 `nano` の新しい接頭辞を追加します：

    ```jldoctest  julia> ucat = UnitCatalogue([], [])  UnitCatalogue providing   0 unit prefixes   0 base units

    julia> nano = UnitPrefix(name="nano", symbol="n", value=1e-9)  UnitPrefix nano (n) of value 1e-9

    julia> add!(ucat, nano)  UnitCatalogue providing   1 unit prefixes   0 base units

    julia> ucat.nano  UnitPrefix nano (n) of value 1e-9  ```
