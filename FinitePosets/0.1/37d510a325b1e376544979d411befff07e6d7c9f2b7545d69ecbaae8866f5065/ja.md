このパッケージは有限ポセットを扱います。

ポセットには2種類あります。「標準ポセット」または `CPoset` は要素 `1:n` 上にあり、ここで `n=length(P)` です。`Poset` は任意の型の要素のリスト上にあります。`Poset` は内部に要素のインデックスで動作する `CPoset` を含んでおり、要素自体で動作するよりも効率的です。効率のために、多くの関数は入力をインデックスに変換し、出力を要素に変換することによって内部の `CPoset` で動作します。

`CPoset` `p` には以下のデータのいずれかが含まれています：

  * `hasse(p)`：ポセットのハッセ図を表すリスト：`i` 番目のエントリは、`i` をカバーする要素のリスト（`i` の直後の要素）であり、つまり `i<j` であり、`i<k<j` となる `k` は存在しません。
  * `incidence(p)`：`incidence[i,j]==true` である場合、`i<=j` であることを示すブール行列です。これは時々ポセットの ζ-行列と呼ばれます。

いくつかの計算はインシデンス行列でより良く機能し、他のいくつかはハッセ図で機能します。計算に必要であり、欠けている場合は、上記のデータのいずれかが他方から計算されます。これは大きなポセットの場合、かなりの時間がかかることがあります。

ポセットを定義する方法はいくつかあります。一つの方法はハッセ図を入力することです：

```julia-repl
julia> p=CPoset([[2,3],[4],[4],Int[]])
1<2,3<4
```

上記のように、`p` はカバリング最大チェーンのリストとして表示されます。ポセットに対して同等の要素（同じ要素をカバーし、同じ要素にカバーされる）は、カンマで区切られて一緒に印刷されます。

```julia-repl
julia> length(p) # `p` の要素の数
4

julia> incidence(p)
4×4 Matrix{Bool}:
 1  1  1  1
 0  1  0  1
 0  0  1  1
 0  0  0  1

julia> linear_extension(p) # p に適合する全順序
4-element Vector{Int64}:
 1
 2
 3
 4
```

`Poset` は `CPoset` と要素のリストから構築されます。

```julia-repl
julia> P=Poset(p,[:a,:b,:c,:d])
a<b,c<d

julia> P.C # P に付随する CPoset
1<2,3<4
```

`Poset` の便利なコンストラクタは、ポセットのための `isless` を表す関数と要素のリストを取り、関数を各要素のペアに適用することによって計算されたインシデンス行列からポセットを構築します。`isless` には `<` を実装する関数または `≤` を実装する関数を与えることができます（いずれの場合も `!=` と `and` されます）。

```julia-repl
julia> l=vec(collect(Iterators.product(1:2,1:2)))
4-element Vector{Tuple{Int64, Int64}}:
 (1, 1)
 (2, 1)
 (1, 2)
 (2, 2)

julia> P=Poset((x,y)->all(map(<=,x,y)),l)
(1, 1)<(2, 1),(1, 2)<(2, 2)

julia> eltype(P) # P の要素の型
Tuple{Int64, Int64}

julia> summary(P) # 大きなポセットに便利
"Poset{Tuple{Int64, Int64}} of length 4"
```

ポセットはインシデンス行列からも構築できるため、最後の例は次のように入力することもできます。

```julia-repl
julia> P=Poset(CPoset([all(map(<=,x,y)) for x in l, y in l]),l)
(1, 1)<(2, 1),(1, 2)<(2, 2)
```

`Poset` の印刷の柔軟性は、`show_element` 関数を設定することによって得られます。この関数は、`IO`、ポセット、および印刷する要素のインデックスを引数として取ります：

```julia-repl
julia> P.show_element=(io,p,n)->join(io,p.elements[n],".");

julia> P
1.1<2.1,1.2<2.2

julia> delete!(P,:show_element); # デフォルトに戻す
```

上記のファンシーな印刷は、REPLやpluto、Jupyterで印刷する際にのみ適用されます。デフォルトの印刷は、Julia に再入力できる形式を提供します。

```julia-repl
julia> print(P) 
Poset(CPoset([[2, 3], [4], [4], Int64[]]),[(1, 1), (2, 1), (1, 2), (2, 2)])
```

ポセットは、順序関係を指定するタプルのリストによって指定できます。これらの関係の推移的閉包が計算され、ポセットが構築されるインシデンス行列が得られます。ポセットの要素は、別々に指定されていない場合、タプルに現れるすべての要素です。

```julia-repl
julia> Poset([(:a,:b),(:c,:d)])
a<b
c<d

julia> CPoset([(1,3),(2,5)]) # CPoset は 1:maximum(entries) 上にあります
4
1<3
2<5
```

ポセット `p` の要素 `i` と `j` の間の順序関係 `≤` または `<` を取得するには、単に `≤(p,i,j)` または `<(p,i,j)` を呼び出します。

```julia-repl
julia> ≤(P,(1,1),(2,1))
true

julia> ≤(P.C,1,2) # 同じ
true
```

ポセット内の区間は、厳密または非厳密な境界で計算できます。

```julia-repl
julia> interval(P,≤,(1,2)) # (1,2) より下の要素
2-element Vector{Tuple{Int64, Int64}}:
 (1, 1)
 (1, 2)

julia> interval(P,≥,(1,2)) # (1,2) より上の要素
2-element Vector{Tuple{Int64, Int64}}:
 (1, 2)
 (2, 2)

julia> interval(P,<,(1,2)) # (1,2) より厳密に下の要素
1-element Vector{Tuple{Int64, Int64}}:
 (1, 1)

julia> interval(P,≥,(2,1),≤,(2,2)) # (2,1) と (2,2) の間の要素
2-element Vector{Tuple{Int64, Int64}}:
 (2, 1)
 (2, 2)

julia> interval(P,>,(1,1),<,(2,2)) # 厳密に間の要素
2-element Vector{Tuple{Int64, Int64}}:
 (2, 1)
 (1, 2)

julia> interval(P.C,>,1,<,4) # インデックスに関して
2-element Vector{Int64}:
 2
 3
```

ポセットで利用可能な他の関数のサンプル：

```julia-repl
julia> maximal_chains(P)
2-element Vector{Vector{Tuple{Int64, Int64}}}:
 [(1, 1), (2, 1), (2, 2)]
 [(1, 1), (1, 2), (2, 2)]

julia> height(P) # 最大チェーンの長さ
3

julia> moebius_matrix(P)
4×4 Matrix{Int64}:
 1  -1  -1   1
 0   1   0  -1
 0   0   1  -1
 0   0   0   1

julia> minima(P)
1-element Vector{Tuple{Int64, Int64}}:
 (1, 1)

julia> maxima(P)
1-element Vector{Tuple{Int64, Int64}}:
 (2, 2)

julia> Q=CPoset(:chain,3)
1<2<3

julia> P1=Poset(Q) # 要素 1:3 のポセットに変換
1<2<3

julia> P⊕ P1 # 順序和
(1, 1)<(2, 1),(1, 2)<(2, 2)<1<2<3

julia> P1*P1
(1, 1)<(2, 1)<(3, 1)<(3, 2)<(3, 3)
(1, 1)<(1, 2)<(2, 2)<(3, 2)
(2, 1)<(2, 2)
(1, 2)<(1, 3)<(2, 3)<(3, 3)
(2, 2)<(2, 3)

julia> P1⊗ P1 # 順序積
(1, 1)<(1, 2)<(1, 3)<(2, 1)<(2, 2)<(2, 3)<(3, 1)<(3, 2)<(3, 3)
```

最後に、`showpic(p)` で `p` が `CPoset` または `Poset` の場合、ポセットのグラフィカル表示が得られます。これには `graphviz` の `dot` コマンドがインストールされている必要があります。その後、xdg "open" コマンドを使用して生成された `.png` ファイルを開きます。これはLinuxおよびMacOsで動作しますが、Windowsでは試すことができませんでした。

詳細については、`⊕, ⊗,  +, *, chains, chainpoly, covering_chains, coxeter_matrix, dual, hasse, height, incidence, induced, interval, is_join_semilattice, is_meet_semilattice, linear_extension, linear_extensions, nlinear_extensions, rand_linear_extension, is_linear_extension, maxima, maximal_chains, antichains, minima, moebius, moebius_matrix, partition, showpic, transitive_closure` に関するオンラインヘルプを参照してください。
