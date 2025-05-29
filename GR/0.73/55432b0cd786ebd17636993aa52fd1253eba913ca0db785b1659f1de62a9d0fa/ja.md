```
polarcellarray(xorg::Real, yorg::Real, phimin::Real, phimax::Real, rmin::Real, rmax::Real, imphi::Int, dimr::Int, color)
```

極座標を使用して円盤にマッピングされた二次元カラインデックス配列を表示します。

**パラメータ:**

`xorg` :     世界座標における円盤中心のX座標 `yorg` :     世界座標における円盤中心のY座標 `phimin` :     度単位での円盤セクターの開始角度 `phimax` :     度単位での円盤セクターの終了角度 `rmin` :     世界座標における穴の開いた円盤の内半径 `rmax` :     世界座標における穴の開いた円盤の外半径 `dimiphi`, `dimr` :     カラインデックス配列のPhi (X) および iR (Y) 次元 `color` :     カラインデックス配列

二次元カラインデックス配列は、配列のX軸を角度、Y軸を半径として解釈することによって、結果の画像にマッピングされます。結果の円盤の中心点は `xorg`, `yorg` に位置し、円盤の半径は `rmax` です。
