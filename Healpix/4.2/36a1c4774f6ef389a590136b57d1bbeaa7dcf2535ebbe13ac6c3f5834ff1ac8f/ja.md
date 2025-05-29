```
xyf2loc(x, y, face) -> (z, phi, sintheta, have_sintheta)
```

XYFとしてエンコードされた位置を与えると、$z = cos(\theta)$、`\phi`、およびオプションで$sin(\theta)$の正確な推定値（`have_sintheta`が`true`の場合）を含むタプルを返します。ここで、$\theta$はコラティチュード、$\phi$は経度であり、どちらもラジアンで表現されます。
