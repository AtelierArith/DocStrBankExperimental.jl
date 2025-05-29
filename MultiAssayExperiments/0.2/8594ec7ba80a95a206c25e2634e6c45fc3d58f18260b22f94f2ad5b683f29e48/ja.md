```
expandsampledata(x, experiment[, colnames])
```

選択した `experiment` のすべてまたは一部の列名に対するサンプルデータを含む DataFrame を返します。列は `sampledata(x)` のものと同じです。

`colnames` が指定されている場合、返される `DataFrame` の各行は `colnames` のエントリに対応し、指定された実験のその列に一致するサンプルのデータを含みます。

`colnames` が指定されていない場合、返される `DataFrame` の各行は指定された実験の列に対応します。

要求された列に `samplemap(x)` に一致するサンプルがない場合、エラーが発生します。この関数を呼び出す前に、[`dropunused`](@ref) を使用して各実験から未使用の列を削除してください。

`sampledata(x)` に重複したサンプル名が含まれている場合、警告が発生します。その場合、データは各サンプルの最初のエントリから取得されます。

`samplemap(x)` に異なるサンプルを持つ同じ実験/列名の組み合わせが複数回出現する場合、警告が発生します。その場合、組み合わせの最初の出現が使用されます。

# 例

```jldoctest
julia> using MultiAssayExperiments;

julia> x = MultiAssayExperiments.exampleobject();

julia> expandsampledata(x, "foo")
10×2 DataFrame
 Row │ name      disease 
     │ String    String  
─────┼───────────────────
   1 │ Patient1  good
   2 │ Patient1  good
   3 │ Patient1  good
   4 │ Patient2  bad
   5 │ Patient2  bad
   6 │ Patient2  bad
   7 │ Patient3  good
   8 │ Patient3  good
   9 │ Patient3  good
  10 │ Patient4  bad

julia> expandsampledata(x, "foo", ["foo2", "foo1"])
2×2 DataFrame
 Row │ name      disease 
     │ String    String  
─────┼───────────────────
   1 │ Patient1  good
   2 │ Patient1  good
```
