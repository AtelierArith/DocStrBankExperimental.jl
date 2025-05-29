camera2projmatrix - カメラ構造体からカメラ投影行列を生成する

```
Usage:     P = camera2projmatrix(C)

Argument:  C - カメラ構造体

Returns:   P - 同次3D世界座標を同次画像座標にマッピングする3x4カメラ投影行列。
```

関数はカメラ構造体を受け取り、レンズ歪みパラメータなどを無視してその等価な投影行列を返します。

参照: Camera(), projmatrix2camera(), cameraproject()
