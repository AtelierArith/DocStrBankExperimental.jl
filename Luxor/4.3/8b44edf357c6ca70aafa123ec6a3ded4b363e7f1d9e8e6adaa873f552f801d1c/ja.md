```
polyportion(p::Vector{Point}, portion=0.5; 
    closed=true,
    pdist = Vector{Union{Float64, Int}}[])
```

ポリゴンの一部を返します。開始値は0.0（始まり）から1.0（終わり）の間です。0.5はポリゴンの前半を、0.25は最初の四分の一を、0.75は最初の四分の三を返します。

`closed=false`を使用すると、最終点から最初の点への線を計算から除外します。

ポリゴン内の各点間の距離のリスト（「ポリ距離」）がすでにある場合は、それを`pdist`に渡すことができます。そうでない場合は、`polydistances(p, closed=closed)`を使用して新たに計算されます。

補完的な`polyremainder()`関数を使用して、他の部分を返します。
