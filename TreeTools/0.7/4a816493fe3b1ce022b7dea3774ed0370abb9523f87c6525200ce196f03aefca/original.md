```
is_ancestor(t::Tree, a::AbstractString, n::AbstractString)
is_ancestor(a::TreeNode, n::TreeNode)
```

Check if `a` is an ancestor of `n`, in the sense that `ancestor(ancestor(...(node))) == a`.
