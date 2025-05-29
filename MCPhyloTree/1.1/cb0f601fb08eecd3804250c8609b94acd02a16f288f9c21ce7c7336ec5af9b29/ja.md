```
NNI(root::T)::T  where T<:AbstractNode
```

この関数は、`root`で指定された木に対して最近接隣接交換（NNI）操作を行います。

元の木をそのままにして、変異したコピーを返します。

  * `root` : NNIを実行する木の根ノード。
