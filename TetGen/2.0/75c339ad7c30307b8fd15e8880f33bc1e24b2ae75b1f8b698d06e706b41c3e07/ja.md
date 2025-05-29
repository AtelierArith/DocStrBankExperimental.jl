```julia
mutable struct RawTetGenIO{T}
```

TetGenの内部表現にデータを転送するための構造体です。

TetGenの入力は、3Dポイントセット、3D区分線形複合体（PLC）、または四面体メッシュのいずれかです。入力オブジェクトと指定されたオプションに応じて、TetGenの出力は、デローニ（または重み付きデローニ）四面体分割、制約付き（デローニ）四面体分割、または品質の高い四面体メッシュのいずれかになります。

区分線形複合体（PLC）は、内部境界（サブドメイン）を持つ可能性のある3D多面体領域を表します。これは[Miller et al, 1996]で導入されました。基本的には、「セル」の集合、すなわち頂点、エッジ、多角形、および多面体であり、そのセルの任意の2つの交差は他のセルの和集合です。

'RawTetGenIO'構造体は、ポイント、ファセット、四面体などのデータの配列のコレクションです。すべてのデータはC++の表現と互換性があり、コピーせずに使用できます。

  * `pointlist::Matrix`: 'pointlist': `size(pointlist,1)==3`のポイント座標の配列。
  * `pointattributelist::Matrix`: 'pointattributelist': ポイント属性の配列。ポイントごとの属性の数は`size(pointattributelist,1)`によって決まります。
  * `pointmtrlist::Matrix`: 'pointmtrlist': ポイントでのメトリックテンソルの配列。
  * `pointmarkerlist::Vector{Int32}`: 'pointmarkerlist': ポイントマーカーの配列；ポイントごとに1つの整数。
  * `tetrahedronlist::Matrix{Int32}`: 'tetrahedronlist': `pointlist`のインデックスで表された四面体のコーナーの配列。オプション`-o2`が指定されていない限り、`size(tetrahedronlist,1)==4`、すなわち各列は四面体の4つのコーナーを説明します。そうでない場合、`size(tetrahedronlist,1)==10`で、4つのコーナーの後に6つのエッジの中点が続きます。
  * `tetrahedronattributelist::Matrix`: 'tetrahedronattributelist': 四面体属性の配列。
  * `tetrahedronvolumelist::Vector`: 'tetrahedronvolumelist': 制約の配列、すなわち四面体の体積；入力専用。これは局所的な細分化をトリガーするために使用できます。
  * `neighborlist::Matrix{Int32}`: 'neighborlist': 四面体の隣接リストの配列；要素ごとに4つの整数。出力専用。
  * `facetlist::Array{TetGen.RawFacet{T}, 1} where T`: 'facetlist': ファセットの配列。各エントリはファセットの構造体です。
  * `facetmarkerlist::Vector{Int32}`: 'facetmarkerlist': ファセットマーカーの配列；ファセットごとに1つの整数。
  * `holelist::Matrix`: 'holelist': ホール（体積内）の配列。各ホールは、その内部に厳密に存在するポイントによって与えられます。
  * `regionlist::Matrix`: 'regionlist': 領域（サブドメイン）の配列。各領域は、その内部に厳密に存在するシード（ポイント）によって与えられます。各列について、ポイント座標はインデックス[1]、[2]、および[3]にあり、地域属性はインデックス[4]に、最大体積はインデックス[5]に続きます。

    各地域属性は'A'スイッチを選択した場合にのみ使用され、各体積制約は'a'スイッチ（後に数字が続かない）を選択した場合にのみ使用されることに注意してください。
  * `facetconstraintlist::Matrix`: 'facetconstraintlist': ファセット制約の配列。各制約は、そのファセットのサブフェイスに対する最大面積制約を指定します。各列には、インデックス[1]にファセットマーカー、インデックス[2]にその最大面積制約が含まれています。注意：ファセットマーカーは実際には整数です。
  * `segmentconstraintlist::Matrix`: 'segmentconstraintlist': セグメント制約の配列。各制約は、そのセグメントのサブセグメントに対する最大長さ制約を指定します。各列は、インデックス[1]と[2]にセグメントの2つの端点、インデックス[3]に最大長さ制約を含みます。注意：セグメントの端点は実際には整数です。
  * `trifacelist::Matrix{Int32}`: 'trifacelist': 面（三角形）のコーナーの配列。
  * `trifacemarkerlist::Vector{Int32}`: 'trifacemarkerlist': 面マーカーの配列；面ごとに1つの整数。
  * `edgelist::Matrix{Int32}`: 'edgelist': エッジの端点の配列。
  * `edgemarkerlist::Array{Int32}`: 'edgemarkerlist': エッジマーカーの配列。
