```
copyto!(M::PowerManifoldNested, q, p)
```

値を要素ごとにコピーします。すなわち、`p`のすべての要素`a`と`q`のすべての要素`b`について`copyto!(M.manifold, b, a)`を呼び出します。
