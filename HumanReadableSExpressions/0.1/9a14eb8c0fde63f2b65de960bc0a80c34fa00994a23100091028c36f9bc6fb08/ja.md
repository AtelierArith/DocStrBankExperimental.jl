```
readhrse(hrse::IO; options=HrseReadOptions(); type=nothing)
readhrse(hrse::String; options=HrseReadOptions(); type=nothing)
```

指定されたIOオブジェクトまたは文字列からHRSEファイルを読み込み、対応するJuliaオブジェクトを返します。`options`引数はパーサーの設定に使用できます。リストはベクターとして読み込まれ、ペアはPairとして、シンボルと文字列はStringとして、数値型はパーサーオプションで定義された対応するJulia型として読み込まれます。`type`が指定されている場合、結果はそのStructTypes.StructTypeを使用して指定された型として解析されます。

# 例

```jldoctest
julia> using HumanReadableSExpressions

julia> hrse = """
       alpha:
           1 2 3 4
           5 6
           7 8 9
       beta: (0 . 3)
       gamma:
           a: 1
           b: 2
           c: "c"
       """;

julia> readhrse(hrse)
3-element Vector{Pair{String}}:
 "alpha" => [[1, 2, 3, 4], [5, 6], [7, 8, 9]]
  "beta" => (0 => 3)
 "gamma" => Pair{String}["a" => 1, "b" => 2, "c" => "c"]
```

さらに[`HrseReadOptions`](@ref)を参照してください。
