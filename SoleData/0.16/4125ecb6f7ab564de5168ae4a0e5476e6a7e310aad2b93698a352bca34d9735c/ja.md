```
parsefeature(FT::Type{<:VarFeature}, expr::AbstractString; kwargs...)
```

タイプ `FT` の [`VarFeature`](@ref) をその [`syntaxstring`](@ref) 表現から解析します。

# キーワード引数

  * `featvaltype::Union{Nothing,Type} = nothing`: 特徴の featvaltype (いくつかの特徴、例えば [`UnivariateFeature`](@ref) に推奨);
  * `opening_parenthesis::String = "["`:   式ブロックの開始を示す文字列 (例: `"min[V2]"`);
  * `closing_parenthesis::String = "]"`:   式ブロックの終了を示す文字列 (例: `"min[V2]"`);
  * `additional_feature_aliases = Dict{String,Base.Callable}()`: 文字列を呼び出し可能なものにマッピングする辞書で、カスタムメイドの非標準特徴を解析する際に便利です。デフォルトでは、"avg" や "min" などの特徴が提供されます (詳細は `SoleData.BASE_FEATURE_FUNCTIONS_ALIASES` を参照); 文字列が衝突する場合、提供された追加のエイリアスが標準のものを上書きします;
  * `variable_names_map::Union{Nothing,AbstractDict,AbstractVector} = nothing`: 変数名から変数インデックスへのマッピングで、変数名を持つ `syntaxstring` から解析する際に便利です (例: `"min[Heart rate]"`);
  * `variable_name_prefix::String = "V"`:   変数インデックスに使用されるプレフィックス (例: "V10")。

`variable_names_map` と `variable_name_prefix` の引数は、最大で1つだけ提供する必要があります。

!!! note
    ここでのデフォルトの括弧は、[`SoleLogics.parseformula`](@ref) のものとは異なります。なぜなら、特徴は通常 `Atom` にラップされており、`parseformula` はアトムの `syntaxstring` に括弧文字を許可しないからです。


他にも [`VarFeature`](@ref)、[`featvaltype`](@ref)、[`parsecondition`](@ref) を参照してください。
