```
plot_ellipse!(
            ax::PyObject,
            xy::Tuple{Number,Number};
            width::Number = 10,
            height::Number = 10,
            angle::Number = 0,
            color::String = "black",
            edgecolor::String = color,
            facecolor::String = color,
            alpha::Number = 0.5
)

軸に楕円をプロットします。与えられたもの：

  * `ax` プロットする軸
  * `xy` 楕円の中心
  * `width` 楕円の幅
  * `height` 楕円の高さ
  * `angle` 楕円の回転角
  * `color` 楕円の色
  * `edgecolor` 楕円のエッジカラー
  * `facecolor` 楕円の面の色
  * `alpha` 楕円の透明度
```
