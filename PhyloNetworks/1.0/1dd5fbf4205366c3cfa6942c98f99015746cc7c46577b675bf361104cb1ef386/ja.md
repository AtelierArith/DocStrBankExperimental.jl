```
countquartetsintrees(trees [, taxonmap]; which=:all, weight_byallele=true)
```

`trees` ベクトルで観察されたクワルテットの一致係数 (CF) を計算します。存在する場合、`taxonmap` は各アレル名をその種名にマッピングする辞書であるべきです。ファイルに保存するには、まず [`tablequartetCF`](@ref) を使用してデータフレームに変換します。`which=:all` の場合、すべての4タクソンセットのクワルテット CF が計算されます。（他のオプションはまだ実装されていません。）

アルゴリズムは O(mn⁴) で実行され、ここで m は木の数、n は木の中のティップの数です。

CF は種レベルでのみ計算されます。つまり、遺伝子木が同じ種からの複数のアレルを持っていても、4つの異なる種からなる4タクソンセットを考慮します。4つの異なる種 `a,b,c,d` に対して、各種 (`a` など) からのすべてのアレルがクワルテット CF を計算するために考慮されます。

デフォルトでは、各遺伝子の重みは1です。したがって、特定の遺伝子に `n_a` のアレルが `a` から、`n_b` のアレルが `b` から、などがある場合、4つのアレルのセットは `1/(n_a n_b n_c n_c)` の重みを持ち、`a,b,c,d` の CF の計算に使用されます。オプション `weight_byallele=true` を使用すると、4つのアレルのセットには代わりに重み1が与えられます。これにより、クワルテット CF を計算するために使用されるセットの総数が増加します（遺伝子の数よりも大きくなることがあります）。アレルの数が遺伝子間で異なる場合、アレルの数が多い遺伝子にはより多くの重みが与えられるため、CF 値にも影響を与える可能性があります。

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

julia> length(q) # 6タクソンの15の4タクソンセット
15

julia> q[1] # 両方の木が AB|CD に同意: 解像度 1
4-taxon set number 1; taxon numbers: 1,2,3,4
data: [1.0, 0.0, 0.0, 2.0]

julia> q[8] # 木 2 は O (タクソン 6) が欠けており、木 1 は解像度 3 を望む: AO|CD
4-taxon set number 8; taxon numbers: 1,3,4,6
data: [0.0, 0.0, 1.0, 1.0]

julia> q[11] # 木 1 は ACEO が未解決で、木 2 は O が欠けている: このクワルテットのデータはなし
4-taxon set number 11; taxon numbers: 1,3,5,6
data: [0.0, 0.0, 0.0, 0.0]
```

次の例では、各木に集団 A からの2つの個体があります。

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

julia> q[3] # 木 2 は O (タクソン 5) が欠けており、a2 は木 1 で未解決。a1B|EO のみ
4-taxon set number 3; taxon numbers: 1,2,4,5
data: [1.0, 0.0, 0.0, 0.5]
```

次に、これらのオブジェクトを [`tablequartetCF`](@ref) を使用してテーブルに変換する方法を示します。出力は `NamedTuple` です。後で、例えば、オプション `copycols=false` を使用してデータフレームに保存できます（多くの4タクソンセットがある場合、列をコピーしないため）。データフレームは視覚化、フィルタリングなどが容易ですが、パフォーマンスは名前付きタプルの方が良い場合があります。

```jldoctest quartet
julia> nt = tablequartetCF(q,t); # 名前付きタプル

julia> using DataFrames

julia> df = DataFrame(nt, copycols=false); # 列データをコピーせずにデータフレームに変換

julia> show(df, allcols=true) # データフレームは名前付きタプルよりもはるかにきれいに表示される
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

`CSV.write` はデータフレームまたは名前付きタプルを入力として受け取り、テーブルをファイルに書き込むことができます。

最後に、以下の例では、集団ごとに複数のアレルを持つ遺伝子木からクワルテット一致係数を計算する際に `weight_byallele=true` を使用する効果と、テーブルに変換する際に情報のない遺伝子を持つ4タクソンセットをフィルタリングする `keepQwithoutgenes=false` の効果を示します。

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
