```
maketree(x::Vector, s::Symbol=:full)
maketree(n::Int, L::Int, s::Symbol=:full)
```

ツリーを返します (BitVector) s=:full の場合、最初の L レベルのすべてのノードは 1 に等しく、他は 0 です。 s=:dwt の場合、最初の L レベルに対応するノードは 1 に等しく、他は 0 です。
