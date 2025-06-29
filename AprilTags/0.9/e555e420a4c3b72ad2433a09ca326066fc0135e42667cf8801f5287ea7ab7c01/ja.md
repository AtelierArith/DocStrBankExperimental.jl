```
homography_to_pose(H, f_width, f_height, c_width, c_height, [taglength = 2.0])
```

3x3 ホモグラフィ行列とカメラモデル（焦点距離と中心）を与えられたとき、タグのポーズを計算します。

ノート

  * Images.jl は、Julia で `::Array` を列優先（すなわち、縦優先）規約として使用します。つまり、`size(img) == (480, 640)`

      * 軸は画像平面の左上隅から始まります（すなわち、画像フレーム）：
      * `width` は左から右へ、
      * `height` は上から下へ。
  * 低レベルの `ccall` でラップされた C ライブラリは、次の規約を使用します（すなわち、カメラフレーム）：

      * `fx == f_width`,
      * `cy == c_height`、および
      * C ライブラリのカメラ座標系：カメラは正の Z 軸に沿って見ており、`x` は右、`y` は下です。

          * C ライブラリは内部的に次に従います：https://docs.opencv.org/3.4/d9/d0c/group__calib3d.html
  * 焦点距離はピクセル単位で指定する必要があります。
  * 戻り値の単位はタグサイズのものであるため、平行移動成分はタグサイズでスケーリングする必要があります。
  * タグ座標は (-1,-1) から (1,1) までであり、すなわちタグサイズは 2 単位の長さを持ちます。

      * オプションで、タグの長さ（メートル単位）を渡すことでスケーリングされた値を返すことができます。
  * 戻り値は `::Matrix{Float64}` です。

関連

`homographytopose`
