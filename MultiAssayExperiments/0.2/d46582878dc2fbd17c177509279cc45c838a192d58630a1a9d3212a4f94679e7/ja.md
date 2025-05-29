```
filtersamplemap(x; samples = nothing, experiments = nothing, colnames = nothing)
```

要求されたサンプル、実験、列名に基づいてサンプルマッピング `DataFrame` をフィルタリングします。 `x` は `MultiAssayExperiment` またはその [`samplemap`](@ref) である可能性があります。

`samples` が `nothing` の場合、フィルタリングには使用されません。それ以外の場合、保持するサンプルを指定する文字列のベクターまたはセットである可能性があります。単一の文字列も指定できます。

`experiments` が `nothing` の場合、フィルタリングには使用されません。それ以外の場合、保持する実験を指定する文字列のベクターまたはセットである可能性があります。単一の文字列も指定できます。

`colnames` が `nothing` の場合、フィルタリングには使用されません。それ以外の場合、保持する列を指定する文字列のベクターまたはセットである可能性があります。単一の文字列も指定できます。

サンプルマッピングの行は、すべての指定されたフィルターを通過した場合にのみ保持されます。

# 例

```jldoctest
julia> using MultiAssayExperiments

julia> x = MultiAssayExperiments.exampleobject();

julia> filtersamplemap(samplemap(x); samples = ["Patient1", "Patient2"])
8×3 DataFrame
 Row │ sample    experiment  colname 
     │ String    String      String  
─────┼───────────────────────────────
   1 │ Patient1  foo         foo1
   2 │ Patient1  foo         foo2
   3 │ Patient1  foo         foo3
   4 │ Patient2  foo         foo4
   5 │ Patient2  foo         foo5
   6 │ Patient2  foo         foo6
   7 │ Patient2  bar         bar1
   8 │ Patient2  bar         bar2

julia> filtersamplemap(samplemap(x); experiments = "foo")
10×3 DataFrame
 Row │ sample    experiment  colname 
     │ String    String      String  
─────┼───────────────────────────────
   1 │ Patient1  foo         foo1
   2 │ Patient1  foo         foo2
   3 │ Patient1  foo         foo3
   4 │ Patient2  foo         foo4
   5 │ Patient2  foo         foo5
   6 │ Patient2  foo         foo6
   7 │ Patient3  foo         foo7
   8 │ Patient3  foo         foo8
   9 │ Patient3  foo         foo9
  10 │ Patient4  foo         foo10
```
