```
polysmooth(points, radius, action=:action; debug=false, close=true)
polysmooth(points, radius; action=:none, debug=false, close=true)
```

`points` から閉じたパスを作成し、指定された半径で角をアークに丸めます。完了したらアクションを実行します。

アークのサイズは時々異なります：指定された半径が最短辺の長さより大きい場合、アークはその全半径で描画できず、したがって最短辺が許す限りできるだけ大きく描画されます。

`debug` オプションは、各コーナーで構造円も描画します。

TODO ブール値よりも有用なものを返す。
