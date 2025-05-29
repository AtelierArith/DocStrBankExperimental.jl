```
Lattice(a, b, c, α, β, γ; axis = :a)
```

六つのセルパラメータから `Lattice` を構築します。

ここで使用したデフォルトの規約は、エッジベクトル 𝐚 が正の x 軸方向、エッジベクトル 𝐛 が x-y 平面内で正の y 軸成分を持ち、エッジベクトル 𝐜 がデカルト座標系で正の z 軸成分を持つことです。詳細は [Wikipedia](https://en.wikipedia.org/w/index.php?title=Fractional_coordinates&oldid=961675499#In_crystallography) を参照してください。`axis = :c` を選択することもできます。
