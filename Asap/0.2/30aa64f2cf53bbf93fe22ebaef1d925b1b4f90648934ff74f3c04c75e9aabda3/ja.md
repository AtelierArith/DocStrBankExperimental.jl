```
fixnode!(node::AbstractNode, fixity::Symbol)
```

ノードの自由度（DOF）を共通の境界条件に固定します。

# 引数

  * `node::AbstractNode` 修正するノード
  * `fixity::Symbol` 適用する境界条件。利用可能な境界条件：

      * :free
      * :fixed
      * :pinned
      * :(x/y/z)free
      * :(x/y/z)fixed
