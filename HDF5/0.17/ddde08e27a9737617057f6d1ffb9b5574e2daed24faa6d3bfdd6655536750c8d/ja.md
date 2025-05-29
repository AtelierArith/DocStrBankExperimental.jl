```
create_dataset(parent, path, datatype, dataspace; properties...)
```

# 引数

  * `parent` - `File` または `Group`
  * `path` - HDF5ファイル内のデータセットのパスを説明する `String` または匿名データセットを作成するための `nothing`
  * `datatype` - データセットの `Datatype` または `Type`
  * `dataspace` - データセットの `Dataspace` または `Dims`
  * `properties` - データセットのプロパティを設定するキーワード名-値ペア

# キーワード

設定できるキーワードプロパティは多数あります。以下は選択されたキーワードのいくつかです。

  * `chunk` - チャンクのサイズを説明する `Dims`。フィルタを適用するために必要です。
  * `filters` - データに適用するフィルタの順序を説明する `AbstractVector{<: Filters.Filter}`。詳細は [`Filters`](@ref) を参照してください。
  * `external` - `Tuple{AbstractString, Intger, Integer}` `(filepath, offset, filesize)` 外部データセットファイルの場所、データオフセット、およびファイルサイズ。詳細は [`API.h5p_set_external`](@ref) を参照してください。

さらに、初期作成、転送、およびアクセスプロパティをキーワードとして提供できます。

  * `dcpl` - [`DatasetCreateProperties`](@ref)
  * `dxpl` - [`DatasetTransferProperties`](@ref)
  * `dapl` - [`DatasetAccessProperties`](@ref)
