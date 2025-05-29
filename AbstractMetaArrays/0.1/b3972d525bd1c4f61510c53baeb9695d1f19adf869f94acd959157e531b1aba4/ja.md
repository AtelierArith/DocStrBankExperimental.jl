SimpleMetaArray{T,N,A<:AbstractArray{T,N}} <: AbstractMetaArray{T,N,A<:AbstractArray{T,N}}

メタデータを持つシンプルな配列のための AbstractMetaArray の具体的な実装です。これは AbstractMetaArray のインスタンスを作成するために使用できる具体的な型です。メタデータと colmetadata フィールドがあり、これらは文字列キーと `Tuple{Any,Symbol}` 型の値を持つ辞書です。

以下のトレイトを使用します：

AbstractMetaArrays.ColMetadataTrait(::Type{<:SimpleMetaArray}) = HasColMetadata()    AbstractMetaArrays.ColMetadataStyle(::Type{<:SimpleMetaArray}) = ReadWriteColMetadata()    AbstractMetaArrays.MetadataStyle(::Type{<:SimpleMetaArray}) = ReadWriteMetadata()

抽象型とそのメソッドに関する詳細は [`AbstractMetaArray`](@ref) を参照してください。
