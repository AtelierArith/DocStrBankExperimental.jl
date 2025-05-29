```
Pattern(image)
Pattern(mask[; color1, color2])
```

`image`（色の行列）または`mask`（実数の行列）から`ImagePattern`を作成します。パターンはプロットに`color`として渡してテクスチャを付けることができます。`mask`が渡された場合、補間される色の間の色を指定することができます。
