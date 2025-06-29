`WGraphToRepresentation(coxrank::Integer,graph,v)`

一変数の岩堀-ヘッケ代数のいくつかの表現を `W`-グラフとして保存します。コクセター系 `(W,S)` に対して、`W`-グラフは、頂点の集合 `C` と、`x∈ C` に対して部分集合 `I(x)⊂ S` を付ける関数 `I` によって定義され、*エッジラベル* は `(x,y)∈ C^2` に `μ(x,y)∈ K` を付けます。ここで `K` は `W` の定義体です。これは、基底 ${e_y}_{y∈ C}$ を持つ空間上で、パラメータ `v` と `-v⁻¹` を持つヘッケ代数の表現を定義します：

$$
Tₛ(e_y)=-e_y
$$

もし `s∈ I(y)` の場合、そうでなければ $Tₛ(e_y)=v^2 e_y+∑_{x∣s∈ I(x)} vμ(x,y)eₓ$ です。

`W`-グラフは、スペースを節約するためにコンパクトな形式で保存されます。これらはペアとして表現されます。

  * 最初の要素は `C` を説明するリストです。その要素は、`eachindex(S)` のインデックスのベクトル `I(x)` であるか、前の要素を `n` 回繰り返すことを指定する整数 `n` です。
  * 2番目の要素は `μ` を指定するリストです。

まず、対称的な `W`-グラフ（`μ(x,y)=μ(y,x)` の場合）のための `μ`-リストを説明します。`μ` によって取られる非ゼロ値 `m` ごとに `μ`-リストの要素が1つあり、その要素は最初の要素が `m` で、2番目の要素がリストのリストであるペアで構成されています。もし `l` がこれらのリストの1つであれば、各ペア `[l[1],l[i]]` はエッジ (`x=l[1]`,`y=l[i]`) を表し、`μ(x,y)=μ(y,x)=m` となります。非対称的な `W`-グラフの場合、`μ`-リストの各ペアの最初の要素はペア `[m1,m2]` であり、2番目の要素のリストから得られる各エッジ `[x,y]` は `μ(x,y)=m1` および `μ(y,x)=m2` と解釈されなければなりません。

```julia-repl
julia> W=coxgroup(:H,3)
H₃

julia> g=Wgraph(W,3)
2-element Vector{Vector{Vector{Any}}}:
 [[2], [1, 2], [1, 3], [1, 3], [2, 3]]
 [[-1, [[1, 3], [2, 4], [3, 5], [4, 5]]]]

julia> WGraphToRepresentation(3,g,Pol(:x))
3-element Vector{Matrix{Pol{Int64}}}:
 [x² 0 … 0 0; 0 -1 … 0 0; … ; 0 0 … -1 -x; 0 0 … 0 x²]
 [-1 0 … 0 0; 0 -1 … -x 0; … ; 0 0 … x² 0; 0 0 … -x -1]
 [x² 0 … 0 0; 0 x² … 0 0; … ; 0 -x … -1 0; 0 0 … 0 -1]
```
