```
reconstruct_axis!(
    daf::DafWriter;
    existing_axis::AbstractString,
    implicit_axis::AbstractString,
    [rename_axis::Maybe{AbstractString} = nothing,
    empty_implicit::Maybe{StorageScalar} = nothing,
    implicit_properties::Maybe{AbstractSet{<:AbstractString}} = nothing,
    properties_defaults::Maybe{AbstractDict} = nothing]
)::AbstractDict{<:AbstractString, Maybe{StorageScalar}}
```

`daf`の`existing_axis`が`implicit_axis`というプロパティを持っている場合、そのプロパティと同じ名前の新しい軸を作成します（または、指定されている場合は`rename_axis`と呼びます）。`empty_implicit`が指定されている場合、このプロパティの値は空文字列に置き換えられます（`existing_axis`エントリに関連付けられた値がないことを示します）。各`implicit_properties`について、`implicit_axis`とプロパティ値とのマッピングを収集し、新しく作成された軸のプロパティとして保存します。

`implicit_axis`がすでに存在する場合、`existing_axis`によって提供されたすべての値が実際に`implicit_axis`のエントリ名として存在することを確認します。これにより、現在使用されていない追加のエントリを持つ`implicit_axis`を手動で作成することができます。

`implicit_properties`が明示的に指定されている場合、`implicit_axis`からのマッピングが一貫していることを要求します。そうでない場合、`existing_axis`のすべてのプロパティを確認し、それぞれのマッピングが一貫しているかどうかをチェックします。一貫している場合、そのプロパティを新しい軸に移行します。たとえば、セルごとのデータを含む`AnnData`をインポートする際、どのプロパティが実際にバッチごとのものであるか（例：セルの年齢）や、どのプロパティが実際にセルごとのものであるか（例：ダブレットスコア）が常に明確ではありません。`implicit_properties`を指定しないことで、関数が自動的に判断できるようになります。

!!! note
    変換された各プロパティについて、`implicit_axis`値がない（つまり、空文字列または`empty_implicit`値を持つ）`existing_axis`エントリに関連付けられた値は失われます。たとえば、各セルタイプに色があるが、一部のセルにはタイプがない場合、「タイプのないセル」の色は失われます。この値が一貫していることを要求し、移行された各プロパティ名とそのようなエントリの値（存在する場合）とのマッピングを返します。元のプロパティを再構築する際には、この値を[`IfNot`](@ref)を使用して指定します（例：`/ cell : type => color ?? magenta`）。

