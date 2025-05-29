```
NNI(root::T, target::T, lor::Bool)::Int64   where T<:AbstractNode
```

この関数は、`root`で指定された木に対して最近接隣接交換（NNI）移動を行います。パラメータ`target`は、ターゲットノードの左または右の子を使用して交換移動を行うノードを指定します。左の子を使用する場合は`lor=true`です。

関数は、移動が成功した場合は1を返し、そうでない場合は0を返します。

  * `root` : NNIを実行する木の根ノード。
  * `target` : 交換する木の特定のノード。
  * `lor` : Bool; "true"は`target`の左の子を使用し、"false"は右の子を使用します。
