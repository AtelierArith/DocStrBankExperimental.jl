```
checkroot!(net)
checkroot!(net::HybridNetwork, membership::Dict{Node, Int})

`net`のルートを適切なノードに設定し、`membership`によって出力された`containroot`フィールドを適切に更新します。ノードがルートツリーエッジコンポーネントに属している場合、それはルートとして適切であり、すなわちツリーエッジコンポーネントグラフのルートです。

  * 現在のルートが適切であれば、そのままにします。エッジの方向（`ischild1`を介して）もそのままにし、既存のルートと同期していると仮定します。
  * そうでない場合、ルートは`net.node`の最初の適切なノードに設定されます。これは葉ではありません。このルートからエッジは外向きに指向されます。

`net`が有効な半方向系系統ネットワークでない場合（すなわち、与えられたハイブリッドエッジと互換性のある方法でネットワークをルートすることができない場合）、`RootMismatch`エラーがスローされます。

出力: ルートコンポーネントの`membership` ID。ルートコンポーネント内のノードの完全なセットは、以下のように取得できます。警告: 2番目のバージョン`checkroot!(net, membership)`を呼び出した後にのみ出力コンポーネントIDを使用してください。

```

jldoctest julia> net = readnewick("(#H1:::0.1,#H2:::0.2,(((b)#H1)#H2,a));");

julia> membership = treeedgecomponents(net);

julia> rootcompID = checkroot!(net, membership);

julia> rootcomp = keys(filter(p -> p.second == rootcompID, membership));

julia> sort([n.number for n in rootcomp]) # ルートコンポーネント内のノードの数 3-element Vector{Int64}:  -3  -2   4 ```
