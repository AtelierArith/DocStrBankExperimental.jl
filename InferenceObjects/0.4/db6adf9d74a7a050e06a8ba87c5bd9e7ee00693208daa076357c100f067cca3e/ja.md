```
InferenceData{group_names,group_types}
```

次元データを使用した推論データストレージのためのコンテナ。

このオブジェクトは、[InferenceData スキーマ](@extref arviz schema)を実装しています。

内部的には、グループは `NamedTuple` に格納されており、`parent(::InferenceData)` を使用してアクセスできます。

# コンストラクタ

```
InferenceData(groups::NamedTuple)
InferenceData(; groups...)
```

`NamedTuple` またはグループのキーワード引数から推論データを構築します。

グループは [`Dataset`](@ref) オブジェクトでなければなりません。

[`InferenceData`](@ref) を直接作成する代わりに、エクスポートされた `from_xyz` 関数または [`convert_to_inference_data`](@ref) を使用してください。
