The expression `children(tree,node)` returns an iterator that will produce a sequence of nodes. These values do not have a lot of meaning by themselves, but can be used in conjunction with the tree object. E.g:

```
data(tree, node_itr)
children(tree, node_itr)
```

In fact, the node iterators should be regarded as lightweight proxies for the underlying node and their attached data payload. The node objects themselves are of limited use for the client programmer as they are an implementation detail of the specific tree being used.
