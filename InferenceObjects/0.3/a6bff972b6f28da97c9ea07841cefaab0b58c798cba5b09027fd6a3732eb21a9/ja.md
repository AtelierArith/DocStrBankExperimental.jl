```
convert_to_inference_data(obj; group, kwargs...) -> InferenceData
```

サポートされているオブジェクトを[`InferenceData`](@ref)オブジェクトに変換します。

`obj`が単一のデータセットに変換される場合、`group`は結果の`InferenceData`内のどのデータセットであるかを指定します。

[`convert_to_dataset`](@ref)を参照してください。

# 引数

  * `obj`は多くのオブジェクトを持つことができます。基本的なサポートされているタイプは次のとおりです：

      * [`InferenceData`](@ref): 変更せずに返す
      * [`Dataset`](@ref)/`DimensionalData.AbstractDimStack`: `InferenceData`に唯一のグループとして追加
      * `NamedTuple`/`AbstractDict`: 唯一のグループとして`Dataset`を作成
      * `AbstractArray{<:Real}`: 任意の名前が設定されていない場合、唯一のグループとして`Dataset`を作成

より具体的なタイプは別途文書化される場合があります。

# キーワード

  * `group::Symbol = :posterior`: `obj`が単一のデータセットに変換される場合、結果のデータセットをこのグループに割り当てます。
  * `dims`: 変数名を次元名を含むオブジェクトのコレクションにマッピングするコレクション。受け入れ可能なオブジェクトは次のとおりです：

      * `Symbol`: 次元名
      * `Type{<:DimensionsionalData.Dimension}`: 次元タイプ
      * `DimensionsionalData.Dimension`: 次元、インデックスを持つ可能性あり
      * `Nothing`: 次元名が提供されていない場合、自動的に次元名が生成されます
  * `coords`: 指定された次元のインデックスを指定する次元名でインデックス可能なコレクション。`dims`内の次元のインデックスが提供されている場合、それらは次元が独自のインデックスを含んでいても使用されます。次元が欠けている場合、そのインデックスは自動的に生成されます。
  * `kwargs`: コンバータ関数に転送される残りのキーワード
