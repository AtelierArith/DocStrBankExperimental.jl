```
convective_derivative(v::Edges,base_cache::BasicILMCache)
```

`v`の対流微分を計算します。すなわち、$v\cdot \nabla v$です。結果は、`base_cache`が`IndexScaling`型か`GridScaling`型かに応じて、1またはグリッドセルサイズで割られます。
