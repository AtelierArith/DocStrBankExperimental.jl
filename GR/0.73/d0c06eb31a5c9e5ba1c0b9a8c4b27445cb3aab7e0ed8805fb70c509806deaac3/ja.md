```
nonuniformcellarray(x, y, dimx::Int, dimy::Int, color)
```

非均一セルサイズの2次元カラーインデックス配列を表示します。

**パラメータ:**

`x`, `y` :     セルのエッジのXおよびY座標 `dimx`, `dimy` :     カラーインデックス配列のXおよびY次元 `color` :     カラーインデックス配列

`x` と `y` の値はワールド座標で表されます。`x` には `dimx` + 1 要素が含まれ、`y` には `dimy` + 1 要素が含まれている必要があります。要素 i と i+1 はそれぞれXおよびY方向のi番目のセルのエッジです。
