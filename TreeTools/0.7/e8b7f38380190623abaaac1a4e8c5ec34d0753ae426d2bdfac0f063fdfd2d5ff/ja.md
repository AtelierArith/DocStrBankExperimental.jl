```
node2tree(root::TreeNode{T}; label = default_tree_label(), force_new_labels=false)
```

`root` から `label` という名前の `Tree` オブジェクトを作成します。 `force_new_labels` が真の場合、ノードラベルにランダムな文字列が追加されて一意にします。
