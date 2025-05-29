```
getpartneredge(edge::Edge)
getpartneredge(edge::Edge, node::Node)
```

`edge`のハイブリッドパートナーである`Edge`、つまり`edge`と同じ子ノード`node`を持つことを意味します。この子ノード`node`は、2番目のメソッドの引数として与えられます。前提条件は、チェックされていません：

  * 入ってくる多分岐はない：ノードは0、1、または2の親を持ち、それ以上はありません
  * `node`が与えられた場合、それは`edge`の子であると仮定されます（最初のメソッドは2番目のメソッドを呼び出します）。

参照：[`getparent`](@ref)、[`getchild`](@ref)
