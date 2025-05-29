```
configmodel!(net::FastNet,degreedist;<keyword arguments>)
```

指定された次数分布 *degreedist* を持つ構成モデルスタイルのネットワークを作成します。

*net* のネットワークは新しいトポロジーに置き換えられます。次数分布は、*degreedist[k]* が、ランダムに選ばれたノードが次数 k を持つ確率 p<sub>k</sub> を指定する Float64 変数のベクトルとして指定されます。*degreedist* の要素の合計が 1.0 未満の場合、残りのノードは次数ゼロになります。

ネットワーク生成は高速で偏りがありませんが、単純グラフになることは保証されていません。アルゴリズムは、可能な限り希望する次数分布に一致させようとしますが、次数分布が奇数の次数の合計や特定の次数のノードの非整数数をもたらす場合、小さな不一致が生じることがあります。

FastNet が希望するリンク数またはノード数を収容するのに十分でない場合、引数エラーが発生します。

キーワード引数は次のとおりです。

  * N : ネットワークの作成に使用されるノードの数
  * S : ノードの状態。この状態にすべてのノードが設定されます。

# 例

```jldoctest
julia> using Fastnet

julia> net=FastNet(1000,2000,2,[])
Network of 0 nodes and 0 links

julia> configmodel!(net,[0.5,0.25,0.25],N=200)
Network of 200 nodes and 175 links

julia> degreedist(net)
3-element Vector{Float64}:
 0.5
 0.25
 0.25

julia> configmodel!(net,[0.5,0.25],N=200)
Network of 200 nodes and 100 links

julia> degreedist(net)
2-element Vector{Float64}:
 0.5
 0.25
```
