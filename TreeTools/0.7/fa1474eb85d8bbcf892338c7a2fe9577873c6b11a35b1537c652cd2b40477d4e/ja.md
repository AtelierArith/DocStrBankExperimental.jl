```
distance(t::Tree, n1::AbstractString, n2::AbstractString; topological=false)
distance(n1::TreeNode, n2::TreeNode; topological=false)
```

`n1`と`n2`の間の枝の長さの距離を、`branch_length`の値を合計することで計算します。`topological`が`true`の場合、代わりに値`1.`が合計され、2つのノードを分ける枝の数がカウントされます（*注意*: 出力は`Int`ではありません！）。
