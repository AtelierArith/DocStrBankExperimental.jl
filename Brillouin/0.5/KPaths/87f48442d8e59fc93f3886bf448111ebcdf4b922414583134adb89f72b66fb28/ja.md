```
interpolate(kp::KPath, N::Integer)
interpolate(kp::KPath; N::Integer, density::Real) --> KPathInterpolant
```

`kp`の補間を返し、全**k**-パスにわたってほぼ等間隔に分布した`N`ポイントを持ちます（等間隔は直交座標系のメトリックで測定されます）。

補間は、等間隔を改善するために`N`よりもわずかに少ないまたは多いポイントを含む場合があります（通常は少ない）。`N`はキーワード引数としても提供できます。

`N`を介して希望する補間ポイントの総数を指定する代わりに、キーワード引数`density`を介して単位（逆）長さあたりの希望する密度を指定することもできます。
