```
polyremainder(p::Vector{Point}, portion=0.5;
    closed=true,
    pdist=Vector{Union{Float64, Int}}[])
```

ポリゴンの残りの部分を返します。開始値は0.0（始まり）から1.0（終わり）までの間です。0.5はポリゴンの後半を返し、0.25は最後の四分の三を、0.75は最後の四分の一を返します。

`closed=false`を使用すると、最終点と最初の点を結ぶ線を計算から除外できます。

ポリゴン内の各点間の距離のリスト（「ポリ距離」）をすでに持っている場合は、それを`pdist`に渡すことができます。そうでない場合は、`polydistances(p, closed=closed)`を使用して新たに計算されます。

補完的な`polyportion()`関数を使用して、もう一方の部分を返します。
