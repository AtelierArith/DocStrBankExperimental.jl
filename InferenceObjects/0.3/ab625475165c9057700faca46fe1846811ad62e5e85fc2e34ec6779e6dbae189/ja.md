```
InferenceData{group_names,group_types}
```

次元データを使用した推論データストレージのためのコンテナ。

このオブジェクトは、[InferenceDataスキーマ](https://python.arviz.org/en/latest/schema/schema.html)を実装しています。

内部的には、グループは`NamedTuple`に格納されており、`parent(::InferenceData)`を使用してアクセスできます。

# コンストラクタ

```
InferenceData(groups::NamedTuple)
InferenceData(; groups...)
```

`NamedTuple`またはグループのキーワード引数から推論データを構築します。

グループは[`Dataset`](@ref)オブジェクトでなければなりません。

`InferenceData`を直接作成するのではなく、エクスポートされた`from_xyz`関数または[`convert_to_inference_data`](@ref)を使用してください。
