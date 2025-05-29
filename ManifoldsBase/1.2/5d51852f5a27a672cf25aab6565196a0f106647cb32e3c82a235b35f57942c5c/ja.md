```
copyto!(M::PowerManifoldNested, q, p)
```

値を要素ごとにコピーします。すなわち、`p`と`q`のすべての要素`a`と`b`について`copyto!(M.manifold, b, a)`を呼び出します。
