```
associate_matrix!(mumps, n, irow, jcol, vals)
```

座標形式で与えられたスパース行列を `Mumps` オブジェクト `mumps` に登録します。この関数を使用することで、ホスト上のみで行列を定義することが可能になります。すべてのノードで行列が定義されている場合、この関数を使用する必要はありません。
