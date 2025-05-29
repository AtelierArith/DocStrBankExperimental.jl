隣接転置を使用して順列を分解するには挿入ソートを使用します。

*隣接転置*、または*単純転置*としても知られるものは、形式 (i i+1) の転置であり、ここでは単に数 i として表されます。

バブルソートと挿入ソートは、ある意味で双対アルゴリズムです（Knuth, TAOCP, Vol 3: Searching and Sort, Sec 5.3.4: Networks for sorting, Figures 45 & 46）。彼らが異なる分解を与える最小の例は、順列:

[1,2,3] ↦ [3,2,1]

も参照してください: [`adjacent_transpositions_by_bubble_sort!`](@ref)。
