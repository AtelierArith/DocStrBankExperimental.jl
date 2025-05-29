```
adjacency!(net,mat;S=1)
```

与えられた隣接行列を持つネットワークを作成します。

*net* のネットワークは、隣接行列 *mat* によって指定された新しいトポロジーで置き換えられます。リンクの方向が重要な場合、要素 *mat[i,j]* は j から i へのリンクに対応します。

対称行列は並行リンクを生成しません。代わりに、リンクは任意の方向に配置されます。

行列内のノード *n* は、作成後に *net* の位置 *n* にあるノードになります。これは必ずしも ID *n* のノードではありません。後で特定のノードを見つける必要がある場合は、adjacency!(net,mat) を呼び出した直後に node(net,pos) 関数を使用してその ID を保存するのが最良です。

*net* が希望するノードまたはリンクの数を収容するのに十分でない場合、引数エラーが発生します。

キーワード引数は次のとおりです。

  * S : ノードの状態。すべてのノードはこの状態に設定されます。

# 例

```jldoctest
julia> using Fastnet

julia> net=FastNet(1000,2000,2,[])
Network of 0 nodes and 0 links

julia> mat=[0 1 0; 1 0 1; 0 1 0]
3×3 Matrix{Int64}:
 0  1  0
 1  0  1
 0  1  0

julia> adjacency!(net,mat)
Network of 3 nodes and 2 links
```
