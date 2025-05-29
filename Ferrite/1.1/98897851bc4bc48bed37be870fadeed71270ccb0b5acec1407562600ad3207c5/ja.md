```
L2Projector(ip::Interpolation, grid::AbstractGrid; [qr_lhs], [set])
```

`L2Projector`を初期化する簡単な方法で、`set`に補間`ip`を追加し、`project`に使用できるように`close!`します。オプションのキーワード引数`set`は`grid`内のすべてのセルがデフォルトとなり、`qr_lhs`は補間`ip`のために質量行列を正確に積分する quadrature ルールがデフォルトとなります。
