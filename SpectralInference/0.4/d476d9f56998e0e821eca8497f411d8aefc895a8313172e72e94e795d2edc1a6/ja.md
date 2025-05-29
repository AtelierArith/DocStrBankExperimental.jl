```
pairedMI_across_treedepth(metacolumns, metacolumns_ids, tree)
pairedMI_across_treedepth(metacolumns, metacolumns_ids, compare::Function=(==), tree::Node; ncuts=100, bootstrap=false, mask=nothing)
```

は各メタカラムを反復処理し、メタカラムのペア要素とツリークラスタのペア要素の間のMIを計算します。

引数:

  * metacolumns: カラムイテレータ、`map(metacolumns)`に供給できます
  * metacolumn_ids: メタカラム内の各要素のID。ツリーのリーフ名と一致する必要がありますが、順序は必ずしも一致する必要はありません。
  * tree: NewickTreeツリー
  * compare: メタカラム内の2つの要素の類似性を計算するために使用される関数。すべてのペアに対してブロードキャストされるため、各要素に対して記述する必要があります。

戻り値:

  * (; MI, treedepths)
  * MI: Vector{Vector{Float64}} 各メタカラムおよび各ツリーデプスのMI
  * treedepths Vector{<:Number} ツリーの各カットに対するツリーデプス（ルートからの距離）
