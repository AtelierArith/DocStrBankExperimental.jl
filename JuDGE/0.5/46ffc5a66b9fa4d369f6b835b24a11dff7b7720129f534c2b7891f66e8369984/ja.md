```
get_node(tree::AbstractTree, indices::Vector{Int})
```

`tree`と`indices`の配列を与えると、この関数は木の中の対応するノードを返します。

### 必要な引数

`tree`はノードを見つけるための木です。

`indicies`は`tree`内のノードを特定する整数インデックスの配列です。

### 例

```
node = get_node(tree,[1]) #ルートノードを取得
node = get_node(tree,[1,1]) #ルートノードの最初の子を取得
node = get_node(tree,[1,2]) #ルートノードの2番目の子を取得
```
