```
countquartetsintrees(trees [, taxonmap]; which=:all, weight_byallele=true)
```

`trees` ベクターで観察されたクワートレットの一致係数 (CF) を計算します。存在する場合、`taxonmap` は各アレル名をその種名にマッピングする辞書であるべきです。ファイルに保存するには、まず [`tablequartetCF`](@ref) を使用してデータフレームに変換します。`which=:all` の場合、すべての 4-タクソンセットのクワートレット CF が計算されます。（他のオプションはまだ実装されていません。）

アルゴリズムは O(mn⁴) で実行され、ここで m は木の数、n は木の中のティップの数です。

CF は種レベルでのみ計算されます。つまり、遺伝子木が同じ種からの複数のアレルを持っていても、4 つの異なる種からなる 4-タクソンセットを考慮します。4 つの異なる種 `a,b,c,d` に対して、各種 (`a` など) からのすべてのアレルがクワートレット CF を計算するために考慮されます。

デフォルトでは、各遺伝子の重みは 1 です。したがって、特定の遺伝子に `n_a` のアレルが `a` から、`n_b` のアレルが `b` からなどある場合、4 つのアレルのセットは、`a,b,c,d` の CF の計算において `1/(n_a n_b n_c n_d)` の重みを持ちます。オプション `weight_byallele=true` を使用すると、4 つのアレルのセットには代わりに重み 1 が与えられます。これにより、クワートレット CF を計算するために使用されるセットの総数が増加します（遺伝子の数よりも大きくなることがあります）。アレルの数が遺伝子間で異なる場合、アレルの数が多い遺伝子にはより多くの重みが与えられるため、CF 値にも影響を与える可能性があります。

# 例

```jldoctest quartet
julia> tree1 = readnewick("(E,(A,B),(C,D),O);"); tree2 = readnewick("(((A,B),(C,D)),E);");

julia> q,t = countquartetsintrees([tree1, tree2]);
Reading in trees, looking at 15 quartets in each...
0+--+100%
  **

julia> t # タクソンの順序: t[i] = タクソン番号 i の名前
6-element Vector{String}:
 "A"
 "B"
 "C"
 "D"
 "E"
 "O"

julia> length(q) # 6 タクソンの 15 の 4-タクソンセット
15

julia> q[1] # 両方の木が AB|CD に同意: 解像度 1
4-taxon set number 1; taxon numbers: 1,2,3,4
data: [1.0, 0.0, 0.0, 2.0]

julia> q[8] # 木 2 は O (タクソン 6) が欠けており、木 1 は解像度 3 を望む: AO|CD
4-taxon set number 8; taxon numbers: 1,3,4,6
data: [0.0, 0.0, 1.0, 1.0]

julia> q[11] # 木 1 は ACEO が未解決で、木 2 は O が欠けている: このクワートレットのデータはありません
4-taxon set number 11; taxon numbers: 1,3,5,6
data: [0.0, 0.0, 0.0, 0.0]
```

次の例では、各木に集団 A からの 2 つの個体があります。

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

julia> q[1] # 木 1 は不一致: a1B|DE と a2D|BE。木 2 は A の両方のアレルに対して AE|BD を持つ
4-taxon set number 1; taxon numbers: 1,2,3,4
data: [0.25, 0.25, 0.5, 2.0]

julia> q[3] # 木 2 は O (タクソン 5) が欠けており、a2 は木 1 で未解決です。a1B|EO のみがあります
4-taxon set number 3; taxon numbers: 1,2,4,5
data: [1.0, 0.0, 0.0, 0.5]
```

次に、これらのオブジェクトを [`tablequartetCF`](@ref) を使用してテーブルに変換する方法を示します。出力は `NamedTuple` です。後で、例えば、オプション `copycols=false` を使用してデータフレームに保存できます（多くの 4-タクソンセットがある場合、列をコピーしないため）。データフレームは視覚化やフィルタリングが容易ですが、パフォーマンスは名前付きタプルの方が良い場合があります。

```jldoctest quartet
julia> nt = tablequartetCF(q,t); # 名前付きタプル

julia> using DataFrames

julia> df = DataFrame(nt, copycols=false); # 列データをコピーせずにデータフレームに変換

julia> show(df, allcols=true) # データフレームは名前付きタプルよりもはるかにきれいに表示されます
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

`CSV.write` は、テーブルをファイルに書き込むためにデータフレームまたは名前付きタプルを入力として受け取ることができます。

最後に、以下の例では、集団ごとに複数のアレルを持つ遺伝子木からクワートレット一致係数を計算する際に `weight_byallele=true` を使用する効果と、テーブルに変換する際に `keepQwithoutgenes=false` を使用して情報のない遺伝子を持つ 4-タクソンセットを除外する効果を示します。

```jldoctest quartet
julia> tree2 = readnewick("((A,(B,D)),E);");

julia> q,t = countquartetsintrees([tree1, tree2], Dict("a1"=>"A", "a2"=>"A"); weight_byallele=true);
Reading in trees, looking at 5 quartets in each...
0+--+100%
  **

julia> nt = tablequartetCF(q,t; keepQwithoutgenes=false); # qind=5 除外: 0 遺伝子

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
