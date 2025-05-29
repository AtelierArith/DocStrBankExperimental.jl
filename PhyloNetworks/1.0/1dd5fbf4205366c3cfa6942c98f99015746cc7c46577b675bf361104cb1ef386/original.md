```
countquartetsintrees(trees [, taxonmap]; which=:all, weight_byallele=true)
```

Calculate the quartet concordance factors (CF) observed in the `trees` vector. If present, `taxonmap` should be a dictionary that maps each allele name to it's species name. To save to a file, first convert to a data frame using [`tablequartetCF`](@ref). When `which=:all`, quartet CFs are calculated for all 4-taxon sets. (Other options are not implemented yet.)

The algorithm runs in O(mn⁴) where m is the number of trees and n is the number of tips in the trees.

CFs are calculated at the species level only, that is, considering 4-taxon sets made of 4 distinct species, even if the gene trees may have multiple alleles from the same species. For 4 distinct species `a,b,c,d`, all alleles from each species (`a` etc.) will be considered to calculate the quartet CF.

By default, each gene has a weight of 1. So if there are `n_a` alleles from `a`, `n_b` alleles from `b` etc. in a given gene, then each set of 4 alleles has a weight of `1/(n_a n_b b_c n_c)` in the calculation of the CF for `a,b,c,d`. With option `weight_byallele=true`, then each set of 4 alleles is given a weight of 1 instead. This inflates the total number of sets used to calculate the quartet CFs (to something larger than the number of genes). This may also affect the CF values if the number of alleles varies across genes: genes with more alleles will be given more weight.

# examples

```jldoctest quartet
julia> tree1 = readnewick("(E,(A,B),(C,D),O);"); tree2 = readnewick("(((A,B),(C,D)),E);");

julia> q,t = countquartetsintrees([tree1, tree2]);
Reading in trees, looking at 15 quartets in each...
0+--+100%
  **

julia> t # taxon order: t[i] = name of taxon number i
6-element Vector{String}:
 "A"
 "B"
 "C"
 "D"
 "E"
 "O"

julia> length(q) # 15 four-taxon sets on 6 taxa
15

julia> q[1] # both trees agree on AB|CD: resolution 1
4-taxon set number 1; taxon numbers: 1,2,3,4
data: [1.0, 0.0, 0.0, 2.0]

julia> q[8] # tree 2 is missing O (taxon 6), tree 1 wants resolution 3: AO|CD
4-taxon set number 8; taxon numbers: 1,3,4,6
data: [0.0, 0.0, 1.0, 1.0]

julia> q[11] # tree 1 has ACEO unresolved, and tree 2 is missing O: no data for this quartet
4-taxon set number 11; taxon numbers: 1,3,5,6
data: [0.0, 0.0, 0.0, 0.0]
```

In the next example, each tree has 2 individuals from population A.

```jldoctest quartet
julia> tree1 = readnewick("(E,(a1,B),(a2,D),O);"); tree2 = readnewick("(((a1,a2),(B,D)),E);");

julia> q,t = countquartetsintrees([tree1, tree2], Dict("a1"=>"A", "a2"=>"A"); showprogressbar=false);

julia> t
5-element Vector{String}:
 "A"
 "B"
 "D"
 "E"
 "O"

julia> q[1] # tree 1 has discordance: a1B|DE and a2D|BE. tree 2 has AE|BD for both alleles of A
4-taxon set number 1; taxon numbers: 1,2,3,4
data: [0.25, 0.25, 0.5, 2.0]

julia> q[3] # tree 2 is missing O (taxon 5), and a2 is unresolved in tree 1. There's only a1B|EO
4-taxon set number 3; taxon numbers: 1,2,4,5
data: [1.0, 0.0, 0.0, 0.5]
```

Next we show how to convert these objects to a table using [`tablequartetCF`](@ref). The output is a `NamedTuple`. It can be saved later to a `DataFrame` for example, using option `copycols=false` to avoid copying the columns (which can be very large if there are many 4-taxon sets). Data frames are easier to visualize, filter etc., but performance can be better on named tuples.

```jldoctest quartet
julia> nt = tablequartetCF(q,t); # named tuple

julia> using DataFrames

julia> df = DataFrame(nt, copycols=false); # convert to a data frame, without copying the column data

julia> show(df, allcols=true) # data frames are displayed much more nicely than named tuples
5×9 DataFrame
 Row │ qind   t1      t2      t3      t4      CF12_34  CF13_24  CF14_23  ngenes  
     │ Int64  String  String  String  String  Float64  Float64  Float64  Float64 
─────┼───────────────────────────────────────────────────────────────────────────
   1 │     1  A       B       D       E          0.25     0.25      0.5      2.0
   2 │     2  A       B       D       O          0.5      0.5       0.0      1.0
   3 │     3  A       B       E       O          1.0      0.0       0.0      0.5
   4 │     4  A       D       E       O          1.0      0.0       0.0      0.5
   5 │     5  B       D       E       O          0.0      0.0       0.0      0.0

julia> # using CSV; CSV.write(nt, "filename.csv");
```

Note that `CSV.write` can take a data frame or a named tuple as input, to write the table to a file.

Finally, the example below shows the effect of using `weight_byallele=true` when caculating quartet concordance factors from gene trees with multiple alleles per population, and of filtering out 4-taxon sets with no informative genes with `keepQwithoutgenes=false` when converting to a table.

```jldoctest quartet
julia> tree2 = readnewick("((A,(B,D)),E);");

julia> q,t = countquartetsintrees([tree1, tree2], Dict("a1"=>"A", "a2"=>"A"); weight_byallele=true);
Reading in trees, looking at 5 quartets in each...
0+--+100%
  **

julia> nt = tablequartetCF(q,t; keepQwithoutgenes=false); # qind=5 excluded: 0 genes

julia> show(DataFrame(nt, copycols=false), allcols=true)
4×9 DataFrame
 Row │ qind   t1      t2      t3      t4      CF12_34   CF13_24   CF14_23   ngenes  
     │ Int64  String  String  String  String  Float64   Float64   Float64   Float64 
─────┼──────────────────────────────────────────────────────────────────────────────
   1 │     1  A       B       D       E       0.333333  0.333333  0.333333      3.0
   2 │     2  A       B       D       O       0.5       0.5       0.0           2.0
   3 │     3  A       B       E       O       1.0       0.0       0.0           1.0
   4 │     4  A       D       E       O       1.0       0.0       0.0           1.0
```
