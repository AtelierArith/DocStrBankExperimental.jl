```
translate_to!(molecule, xf)
translate_to!(molecule, x)
translate_to!(molecule, xf, box)
translate_to!(molecule, x, box)
```

分子を移動させて、その質量中心が分数座標空間の点 `xf` に、または直交座標空間の点 `x` に位置するようにします。後者の場合、文脈のために単位セルボックスが必要です。
