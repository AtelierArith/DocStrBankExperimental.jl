```
concatenate!(
    destination::DafWriter,
    axis::Union{AbstractString, AbstractVector{<:AbstractString}},
    sources::AbstractVector{<:DafReader};
    [names::Maybe{AbstractVector{<:AbstractString}} = nothing,
    dataset_axis::Maybe{AbstractString} = "dataset",
    dataset_property::Bool = true,
    prefix::Union{Bool, AbstractVector{Bool}} = false,
    prefixed::Maybe{Union{AbstractSet{<:AbstractString}, AbstractVector{<:AbstractSet{<:AbstractString}}}} = nothing,
    empty::Maybe{EmptyData} = nothing,
    sparse_if_saves_storage_fraction::AbstractFloat = 0.25,
    merge::Maybe{MergeData} = nothing,
    overwrite::Bool = false]
)::Nothing
```

`sources` の `Daf` データセットのシーケンスから、1つまたは複数の連結 `axis` に沿って単一の `destination` データセットにデータを連結します。`axis` 名の配列を指定することで、複数の軸に沿って連結することもできます。

連結された各データセットには一意の名前が必要です。デフォルトでは、`DafReader.name` を使用します。明示的な `names` ベクターを指定することでこれを上書きできます。

デフォルトでは、連結されたデータセットごとに1つのエントリを持つ新しい軸が `dataset_axis` によって作成され、これらの一意の名前が使用されます。これを無効にするには、`dataset_axis` を `nothing` に設定します。

軸が作成され、`dataset_property` が設定されている場合（デフォルト）、連結された `axis` の同じ名前のプロパティが作成され、各エントリが収集されたデータセットの名前が含まれます。

各連結された軸のエントリは一意でなければなりません。デフォルトでは、エントリ名が1つのデータセットでしか使用されないことを要求します。これが当てはまらない場合は、`prefix` を設定して一意のデータセット名（および `.` 区切り）をそのエントリに追加することを指定します（すべての軸に対して一度、または軸ごとに設定を持つベクターを使用して）。

!!! note
    軸エントリ名にプレフィックスが追加される場合、軸のエントリの値であるすべてのベクタープロパティにも追加する必要があります。デフォルトでは、軸名と同じプロパティ名はそのようなプロパティであると仮定します（例：`cluster` 軸がある場合、各 `cell` の `cluster` プロパティはその軸からのクラスターの名前を含むと仮定されます）。また、プロパティ名が軸名で始まり、その後に `.` といくつかの接尾辞が続くことも許可します（例：`cluster.manual` もクラスターの名前を含むと仮定されます）。このようなすべてのプロパティに一意のプレフィックスを自動的に追加します。

    ただし、このヒューリスティックが失敗した場合、`prefixed` されるプロパティのベクター（またはそのようなベクターのベクター、連結された軸ごとに1つ）を指定できます。この場合、リストされたプロパティのみが一意のデータセット名でプレフィックスされます。


`axis` のベクターおよび行列プロパティは連結されます。連結されたデータセットのいくつかが特定のプロパティを含まない場合、そのために `empty` 値を指定する必要があり、欠損データに使用されます。

連結された行列は常に列優先レイアウトで保存され、連結軸は列軸です。両方の軸が連結された行列は存在してはなりません（例：連結軸の正方行列）。

連結されたプロパティは、スパースデータのストレージが単純な密なストレージよりも `sparse_if_saves_storage_fraction` だけ小さい場合にスパースになります（デフォルトでは、スパースストレージを使用すると、少なくとも25％のスペースが節約される、つまり、密なストレージスペースの最大75％を占める場合）。この割合を推定する際、密なデータは100％非ゼロであると仮定します。すでにスパースとして保存されているデータと、`empty` 値がゼロの欠損データのみを考慮します。

デフォルトでは、連結 `axis` に適用されないプロパティは無視されます。`merge` が指定されている場合、そのようなプロパティはそれに従って処理されます。プロパティに `CollectAxis` を使用するには、`dataset_axis` が `nothing` でない必要があります。

デフォルトでは、連結はターゲット内の既存のプロパティを `overwrite` するのではなく、失敗します。
