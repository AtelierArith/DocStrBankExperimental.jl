```
shiftedkernel = centered(kernel)
```

`kernel`の座標の原点を中心に移動します。`kernel`の中心要素には`shiftedkernel[0, 0, ...]`でアクセスできます。

この関数は、通常の配列を使用してカーネルを簡単に提供できるようにし、任意の軸をサポートしていない他の言語との互換性を提供します。

関連情報: [`imfilter`](@ref).
