```julia
get_branch(diagram, code)

```

`code`という`Int`値のタプルを使用して、図を再帰的に下っていくことで、図の一部（分岐図）を返します。例えば、`get_branch(diagram, (1,2,3,))`は`diagram.child[1].child[2].child[3]`を返します。
