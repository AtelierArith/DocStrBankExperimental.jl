AbstractMetaArray{T,N,A<:AbstractArray{T,N}} <: AbstractArray{T,N}

AbstractMetaArrayは、メタデータとオプションの列メタデータを持つメタ配列を表す抽象型です。これはAbstractArrayのサブタイプであり、すべてのメタ配列に共通のインターフェースを提供します。AbstractMetaArrayのすべての具体的な実装は、この型を継承する必要があります。型パラメータは次のとおりです。

  * `T`: 配列の要素型。
  * `N`: 配列の次元数。
  * `A`: 配列の具体的な型。これはAbstractArray{T,N}のサブタイプである必要があります。

AbstractMetaArrayの具体的な実装は、次のフィールドを定義する必要があります。

  * `_data`: 配列の基礎データ。これはAbstractArray{T,N}のサブタイプである必要があります。
  * `_metadata`: 配列のメタデータ。これは文字列キーと`Tuple{Any,Symbol}`型の値を持つ辞書である必要があります。
  * `_colmetadata`: 配列の列メタデータ。これはシンボルキーと`MetaType`型の値を持つ辞書である必要があります。

AbstractMetaArrayの具体的な実装は、次の特性も定義する必要があります。

  * `ColMetadataTrait`: メタ配列が列メタデータをサポートしているかどうかを定義します。これはColMetadataTraitのサブタイプである必要があります。デフォルトでは、NoColMetadata()です。
  * `ColMetadataStyle`: 列メタデータへのアクセス（読み取り、書き込み、両方、またはなし）を定義します。これはColMetadataStyleのサブタイプである必要があります。
  * `MetadataTrait`: メタ配列がメタデータをサポートしているかどうかを定義します。これはMetadataTraitのサブタイプである必要があります。デフォルトでは、NoMetadata()です。

簡単のために、メタ配列のメタデータと列メタデータを作成するための非公開関数`create_metaarray`が定義されています。これはメタ配列のコンストラクタで使用されます。

具体的なAbstractMetaArrayの実装については[`SimpleMetaArray`](@ref)を参照してください。メタ配列のメタデータと列メタデータを作成するためのヘルパー関数については[`create_metaarray`](@ref)を参照してください。メタ配列が列メタデータをサポートしているかどうかを定義する特性については[`ColMetadataTrait`](@ref)を参照してください。列メタデータへのアクセスを定義する特性については[`ColMetadataStyle`](@ref)を参照してください。メタデータへのアクセスを定義する特性については[`MetadataStyle`](@ref)を参照してください。
