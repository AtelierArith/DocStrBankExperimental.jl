```
getleaf(tree, tree_type)
```

ツリーの葉ノードを返します。

# 引数

  * `tree::BitVector`: 二分木を表すためのBitVector。

# 返り値

`::BitVector`: 二分木を表すことができるBitVectorですが、葉のみが1でラベル付けされ、残りのノードは0でラベル付けされます。

# 例

```@repl
using Wavelets, WaveletsExt

tree = maketree(4, 2, :dwt)     # [1,1,0]
getleaf(tree)                   # [0,0,1,1,1,0,0]
```
