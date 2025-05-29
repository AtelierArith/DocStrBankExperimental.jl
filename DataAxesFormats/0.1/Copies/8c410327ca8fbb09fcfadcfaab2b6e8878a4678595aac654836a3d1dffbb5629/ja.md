```
copy_all!(;
    destination::DafWriter,
    source::DafReader
    [empty::Maybe{EmptyData} = nothing,
    dtypes::Maybe{DataTypes} = nothing,
    overwrite::Bool = false,
    relayout::Bool = true]
)::Nothing
```

`source` [`DafReader`](@ref) のすべての内容を `destination` [`DafWriter`](@ref) にコピーします。`overwrite` が true の場合、ターゲット内の既存のデータは上書きされます。`relayout` が true の場合、行列はソースに保存されている形式に関係なく、ターゲットに両方のレイアウトで保存されます。

これにより、ソースにのみ存在するターゲット軸が作成されますが、`overwrite` の値に関係なく、既存のターゲット軸は**上書きされません**。ターゲットに存在する軸は、ソースの同じ軸と同一であるか、またはその部分集合でなければなりません。

ソースにターゲットの同じ軸の部分集合である軸がある場合、ベクトルおよび/または行列プロパティをコピーする際にターゲットで作成される `empty` エントリの値の辞書を指定する必要があります。これは、ベクトルプロパティの `empty` 値を指定するための `(axis, property) => value` エントリと、行列プロパティの `empty` 値を指定するための `(rows_axis, columns_axis, property) => entry` を使用して指定します。行列プロパティの軸の順序は重要ではありません（同じ `empty` 値が自動的に両方の軸の順序に使用されます）。

`dtype` が指定されている場合、対応するプロパティのコピーされたデータは指定されたデータ型に変換されます。

[`TensorKey`](@ref) が指定されている場合、これは、ソースに存在しないがターゲットに存在するメイン軸のエントリに対して `empty` 値で満たされた行列を作成します。
