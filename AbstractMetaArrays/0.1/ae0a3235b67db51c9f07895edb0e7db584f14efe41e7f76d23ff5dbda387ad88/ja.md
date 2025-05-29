```
module AbstractMetaArrays
```

メタデータとオプションの列メタデータを持つ配列のための抽象インターフェースとユーティリティを提供するJuliaパッケージです。

# 概要

`AbstractMetaArrays`は、標準の`AbstractArray`インターフェースを拡張して、次の機能をサポートする抽象型[`AbstractMetaArray`](@ref)を定義します。

  * **メタデータ**: 配列全体を説明する任意のキー-バリューペア。
  * **列メタデータ**: 個々の列またはコンポーネントに関連付けられたメタデータ（オプション）。

具体的な実装（例えば[`SimpleMetaArray`](@ref)）は`AbstractMetaArray`を継承し、メタデータサポートに対するストレージとトレイトベースの制御を提供します。

# 主な型

  * [`AbstractMetaArray`](@ref): メタ配列のための抽象型。
  * [`AbstractMetaVector`](@ref), [`AbstractMetaMatrix`](@ref): 1Dおよび2Dメタ配列のエイリアス。
  * [`SimpleMetaArray`](@ref): 完全なメタデータと列メタデータサポートを持つ具体的な実装。
  * [`MetaType`](@ref): メタデータ辞書型のエイリアス。

# トレイト

  * [`ColMetadataTrait`](@ref): 列メタデータがサポートされているかどうかを示します。
  * [`ColMetadataStyle`](@ref): 列メタデータへの読み取り/書き込みアクセスを制御します。
  * [`MetadataStyle`](@ref): 配列メタデータへの読み取り/書き込みアクセスを制御します。

# ユーティリティ

  * [`create_metaarray`](@ref): 新しい配列のためのメタデータおよび列メタデータ辞書を構築するためのヘルパー。

# 統合

このパッケージは、標準のメタデータインターフェースのために[DataAPI.jl](https://github.com/JuliaData/DataAPI.jl)と統合され、StaticArraysやStructArraysのようなパッケージとの互換性のための拡張を提供します。

# 例

```julia
using AbstractMetaArrays, StaticArrays

arr = SimpleMetaArray(SVector{3}(1,2,3), Dict("description" => ("test", :entry)), Dict(:x => Dict("unit" => ("m", :default))))
desc = metadata(arr, "description")  # returns "test"
```

カスタムメタ配列を実装し、メタデータサポートを拡張する詳細については、ドキュメントを参照してください。
