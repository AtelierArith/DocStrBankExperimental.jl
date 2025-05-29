```
i = rays(rg::CtGeom)
```

このCTジオメトリのすべての光線の平行ビーム座標を返します。`i`の戻り値の型は`ProductIterator`で、形式は`(u, v, ϕ, θ)`のタプルを作成します。投影を作成するには、`p = [fun(c...) for c in i]`と呼び出します。ここで、`fun`は`radon(...)`です。
