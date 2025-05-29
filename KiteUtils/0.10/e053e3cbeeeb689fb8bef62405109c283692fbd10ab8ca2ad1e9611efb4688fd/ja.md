```
calc_heading(orientation, elevation, azimuth; upwind_dir=-pi/2, respos=true)
```

カイトのヘディング角をラジアンで計算します。ヘディングはカイトの鼻が向いている方向です。オリエンテーションはオイラー角で、北、東、下方向の参照フレームに対して計算されます。もしresposがtrueであれば、ヘディング角は0 .. 2πの範囲で定義され、それ以外の場合は-π .. πの範囲で定義されます。
