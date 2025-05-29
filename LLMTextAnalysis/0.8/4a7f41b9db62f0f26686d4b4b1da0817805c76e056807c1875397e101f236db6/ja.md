```
build_clusters!(index::AbstractDocumentIndex, cls::TrainedClassifier;
    topic_level::AbstractString = "",
    verbose::Bool = true, add_label::Bool = false, add_summary::Bool = false,
    labeler_kwargs::NamedTuple = NamedTuple())
```

分類器のラベルに基づいてトピックを構築し、`index`内のすべての文書に最も高い確率のラベルを付けます。

# 例

```julia
# `index`がすでに構築されており、分類器`cls`もそうであると仮定します
build_clusters!(index, cls; topic_level = "MyClusters")

# 新しいトピックレベルが利用可能であることを確認します
topic_levels(index) |> keys
```
