```
WCSGrid(img::AstroImageMat, ax=(1,2), coords=(first(axes(img,ax[1])),first(axes(img,ax[2]))))
```

AstroImageMatを与えると、画像のピクセル座標に対して物理座標でWCSグリッドラインをプロットするために必要な情報を返します。この関数は、画像座標に投影されたWCSグリッドの回転と一般的な曲率を処理するために、同時に両方のプロットされた軸で機能する必要があります。
