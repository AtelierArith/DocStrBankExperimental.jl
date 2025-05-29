```
updatebox!(box::AbstractVector, x::AbstractArray)
```

別の位置でボックスを更新するか、新しいボックスを作成します。

`box` が正しい次元を持っていない場合、正しいサイズに調整されます。

`box` = 1-D のバウンディングボックス `box=[minx,maxx]`、または 2-D の `box=[minx,maxx,miny,maxy]`、または 3-D の `box=[minx,maxx,miny,maxy,minz,maxz]` です。`box` は、提供された位置 `x` を含むように拡張されます。変数 `x` は、行に複数の点を保持できます。
