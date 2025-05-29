```
namedtuple_to_dataset(data; kwargs...) -> Dataset
```

`NamedTuple`を配列にマッピングする変数名を[`Dataset`](@ref)に変換します。

配列でない値はすべて0次元配列に変換されます。

# キーワード

  * `attrs::AbstractDict{<:AbstractString}`: デフォルトに加えてデータセットに添付するメタデータのコレクション。値はJSONシリアライズ可能である必要があります。
  * `library::Union{String,Module}`: 推論を行うために使用されるライブラリ。`attrs`メタデータに添付されます。
  * `dims`: 変数名をオブジェクトのコレクションにマッピングするコレクションで、次元名を含みます。受け入れ可能なオブジェクトは次のとおりです：

      * `Symbol`: 次元名
      * `Type{<:DimensionsionalData.Dimension}`: 次元タイプ
      * `DimensionsionalData.Dimension`: 次元、インデックスを持つ可能性があります
      * `Nothing`: 次元名が提供されていない場合、自動的に次元名が生成されます
  * `coords`: 次元名でインデックス可能なコレクションで、指定された次元のインデックスを指定します。`dims`内の次元にインデックスが提供されている場合、それらは次元が独自のインデックスを含んでいても使用されます。次元が欠けている場合、そのインデックスは自動的に生成されます。
