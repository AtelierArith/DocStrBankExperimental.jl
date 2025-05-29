```
shownodes(net)
```

FastNet *net* のすべてのノードに関する情報を表示します。

この関数は主にテスト/デバッグのために意図されています。大規模なネットワークに対して呼び出す前に、二度考えることをお勧めします。1000万ノードがあなたのREPLに表示されるのは、思っているほど楽しくありません。

他にも [showlinks](#Fastnet.showlinks) を参照してください。

# 例

```jldoctest julia> using Fastnet

julia> net=FastNet(1000,2000,2,[]);

julia> makenodes!(net,5,1)

julia> makenodes!(net,5,2)

julia> shownodes(net) id      state 1       1 2       1 3       1 4       1 5       1 6       2 7       2 8       2 9       2 10      2
```
