```
ellipseinquad(qgon; action=:none)
ellipseinquad(qgon, action)
```

四角形 `qgon` の内部にフィットするベジエベースの楕円を計算し、現在のパスに追加します。

次の値を返します `ellipsecenter, ellipsesemimajor, ellipsesemiminor, ellipseangle`:

  * `ellipsecenter` 楕円の中心
  * `ellipsesemimajor` 楕円の半長軸
  * `ellipsesemiminor` 楕円の半短軸
  * `ellipseangle` 楕円の回転

適切な楕円が見つからない場合、関数は `O, 0, 0, 0` を返します。（おそらく qgon は凸多角形ではありません。）

## 例

```julia
ellipseinquad(box(O, 130, 130); action = :stroke)
```

```julia
ellipseinquad(box(O, 140, 230), :stroke)
```

### 参考文献

http://faculty.mae.carleton.ca/John_Hayes/Papers/InscribingEllipse.pdf
