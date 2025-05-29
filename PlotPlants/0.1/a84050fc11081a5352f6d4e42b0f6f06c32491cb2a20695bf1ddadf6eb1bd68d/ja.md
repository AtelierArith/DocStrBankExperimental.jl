```
plot_stoma!(
           ax::PyObject,
           xy::Tuple{Number,Number};
           width::Number = 10,
           height::Number = 10,
           stoma::Number = 0.2,
           angle::Number = 0
)

軸上にストマをプロットします。与えられた情報は以下の通りです。

  * `ax` プロットする軸
  * `xy` ストマの中心
  * `width` ストマの幅
  * `height` ストマの高さ
  * `stoma` 気孔の幅比
  * `angle` ストマの回転角度
```
