cameraproject - 3Dポイントをカメラ画像に投影します

```
Usage:             xy = cameraproject(C, pt, computevisibility = false)
        (xy, visible) = cameraproject(C, pt, computevisibility = true)

Arguments:
             C - カメラ構造。
            pt - 画像に投影する3Dポイントの3xN行列。

Keyword Argument:
 computevisibility - trueに設定するとポイントの可視性が返されます
                     デフォルト値はfalseです。

Returns:
       xy      - 投影された画像位置の2xN行列
       visible - ポイントが視野内にあるかどうかを示すブール配列。
                 これは、'computevisibilityがtrueであり、
                 カメラ構造が'rows'および'cols'フィールドに
                 ゼロ以外の値を持つ場合にのみ評価されます。

```

See also: Camera(), camstruct2projmatrix()
