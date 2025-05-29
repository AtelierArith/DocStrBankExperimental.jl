```
CircularPolygon(p::AbstractPath; tol=<default>)
CircularPolygon(p::AbstractVector; tol=<default>)
```

（閉じている可能性のある）パスから、または曲線のベクトルから円形ポリゴンを構築します。`tol`パラメータは、パスの連続性と閉じているかどうかを確認する際に使用される許容誤差です。
