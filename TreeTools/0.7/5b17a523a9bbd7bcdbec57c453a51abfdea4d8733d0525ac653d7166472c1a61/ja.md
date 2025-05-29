```
lca(i_node::TreeNode, j_node::TreeNode)
```

`i_node` と `j_node` の最も低い共通祖先を見つけて返します。アイデアは、より深いノードの側で非対称的に木を上に移動し、両方が根から等しい距離になるまで進むことです。その後、対称的に上に移動することで問題が解決されます。(https://stackoverflow.com/questions/1484473/how-to-find-the-lowest-common-ancestor-of-two-nodes-in-any-binary-tree/6183069#6183069)
