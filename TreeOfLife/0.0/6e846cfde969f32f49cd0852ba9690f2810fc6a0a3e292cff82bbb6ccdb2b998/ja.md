```
getsubtree(oldtree::AbstractTree, tipset; 
	simplify::Bool=true, keeproot::Bool=false) :: AbstractTree
```

与えられたツリーのティップセットから生成されたサブツリーを抽出します。

引数 `simplify` は、内部ノードが子ノードを1つだけ持つ場合に、それを削減する必要があるかどうかを制御します。つまり、子ノードと親ノードを直接接続します。デフォルトでは `true` に設定されています。

引数 `keeproot` は、元のルートノードがサブツリーに含まれる必要があるかどうかを制御します。デフォルトでは `false` に設定されており、言い換えれば、真に最小のスパニングツリー (MST) を生成します。

`simplify` が `false` に設定されている場合、`keeproot` の値は影響を与えません。
