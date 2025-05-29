```
formulas(
    g::AbstractGrammar;
    maxdepth::Integer,
    nformulas::Union{Nothing,Integer} = nothing,
    args...
)::Vector{<:SyntaxBranch}
```

与えられた文法によって生成される有限かつ反復可能なアルファベットの数式を列挙します。

# 実装

追加の `args` を使用して関数の動作をモデル化できます。少なくともこれらの2つの引数をカバーする必要があります：

  * `nformulas` 引数は、返される `Vector` のサイズを制限するために使用できます；
  * `maxdepth` 引数は、構文ツリーとして表される構文コンポーネントを、指定された最大深さに制限するために使用できます；

詳細については、[`AbstractGrammar`](@ref)、[`SyntaxBranch`](@ref)を参照してください。
