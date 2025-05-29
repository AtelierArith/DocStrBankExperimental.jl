```
nauty(g::DenseNauty[Di]Graph; getcanon = false, automgroup = false, partition = nothing) -> NAUTY
```

nautyは、densenautyに依存するnautyへの高レベルインターフェースです。引数はグラフ`g`と、オプションの名前付き引数getcanon::Bool、automgroup::Bool、partitionであり、partitionは`nothing`または生のNauty形式のタプル`(lab,ptn)`、または1から番号付けされた頂点のリストのリストです。

戻り値は、以下のエントリを持つ可変構造体NAUTYです。

  * `orbits::IntDisjointSet`、自動同型群の軌道（1から番号付け）
  * `grpsize::BigInt`、群のサイズ（丸め誤差がある可能性があります）
  * automgroupがtrueの場合、`generators::Vector{Tuple{Permutation,IntDisjointSets,Int}}`、自動同型群の生成元であり、各生成元をこの生成元までの生成元の下の軌道と、これまでの安定化された頂点で表します
  * getcanonがtrueの場合、`lab::Permutation`、古い頂点と新しい頂点の対応、および`canong::typeof(g)`、標準的にラベル付けされたグラフ
