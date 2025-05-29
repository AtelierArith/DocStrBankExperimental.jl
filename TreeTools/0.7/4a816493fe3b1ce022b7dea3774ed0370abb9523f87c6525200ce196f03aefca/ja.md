```
is_ancestor(t::Tree, a::AbstractString, n::AbstractString)
is_ancestor(a::TreeNode, n::TreeNode)
```

`a`が`n`の祖先であるかどうかを確認します。これは、`ancestor(ancestor(...(node))) == a`という意味です。
