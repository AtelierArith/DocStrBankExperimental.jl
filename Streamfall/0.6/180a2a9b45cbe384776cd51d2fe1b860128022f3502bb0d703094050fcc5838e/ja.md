```
create_node(mg::MetaDiGraph, node_name::String, details::AbstractDict, nid::Int)
```

指定された名前のノードを作成します（存在しない場合）。

返り値

  * `this_id` : ノードのID（既存の場合）および
  * `nid` : ネットワーク全体のインクリメントされたノードID（存在する場合は`this_id`と等しい）
