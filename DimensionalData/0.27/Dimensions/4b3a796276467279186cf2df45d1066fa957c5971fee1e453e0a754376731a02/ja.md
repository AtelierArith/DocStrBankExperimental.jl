```
Dim{S}(val=:)
```

汎用次元。ファイルからデータを読み込む際にカスタム次元が必要な場合に使用します。インデックス付けのためのキーワード引数として使用できます。

次元型は、シンボルでインデックス付けを行う際や、例えば Tables.jl のキーを作成する際に同名の `Dim` 型よりも優先されます。

```jldoctest; setup = :(using DimensionalData)
julia> dim = Dim{:custom}(['a', 'b', 'c'])
custom ['a', 'b', 'c']
```
