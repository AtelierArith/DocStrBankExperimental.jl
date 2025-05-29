AbstractMetaArray{T,N,A<:AbstractArray{T,N}} <: AbstractArray{T,N}

AbstractMetaArray is an abstract type that represents a meta array with metadata and optional column metadata.   It is a subtype of AbstractArray and provides a common interface for all meta arrays. All the concrete implementations of   AbstractMetaArray should inherit from this type.   The type parameters are:

  * `T`: The element type of the array.
  * `N`: The number of dimensions of the array.
  * `A`: The concrete type of the array. It should be a subtype of AbstractArray{T,N}.

The concrete implementations of AbstractMetaArray should define the following fields:

  * `_data`: The underlying data of the array. It should be a subtype of AbstractArray{T,N}.
  * `_metadata`: The metadata of the array. It should be a dictionary with string keys and values of type `Tuple{Any,Symbol}`.
  * `_colmetadata`: The column metadata of the array. It should be a dictionary with symbol keys and values of type `MetaType`.

The concrete implementations of AbstractMetaArray should also define the following traits:

  * `ColMetadataTrait`: Defines if the meta array supports column metadata or not. It should be a subtype of ColMetadataTrait. By default, it is NoColMetadata().
  * `ColMetadataStyle`: Defines the access to the column metadata (reading, writing, both, or none). It should be a subtype of ColMetadataStyle.
  * `MetadataTrait`: Defines if the meta array supports metadata or not. It should be a subtype of MetadataTrait. By default, it is NoMetadata().

For simplicity a non exported function `create_metaarray` is defined to create the metadata and colmetadata for the meta array.   It is used in the constructor of the meta array.

See also [`SimpleMetaArray`](@ref) for a concrete implementation of the AbstractMetaArray.     [`create_metaarray`](@ref) for a helper function to create the metadata and colmetadata for the meta array.     [`ColMetadataTrait`](@ref) for the trait that defines if the meta array supports column metadata or not.     [`ColMetadataStyle`](@ref) for the trait that defines the access to the column metadata.     [`MetadataStyle`](@ref) for the trait that defines the access to the metadata.
