隣接置換を隣接交換を用いて分解します。

*隣接置換*（または*単純置換*）は、形式 (i i+1) の置換であり、ここでは単に数 i として表されます。

このアルゴリズムは、Jonathan Huang の博士論文「Probabilistic reasoning and learning on permutations: Exploiting structural decompositions of the symmetric group」のアルゴリズム 2.7 として登場します。Huang が指摘するように、このアルゴリズムはよく知られたバブルソートに非常に似ています。二次の計算量を持っています。

また、[`adjacent_transpositions_by_insertion_sort!`](@ref) も参照してください。
