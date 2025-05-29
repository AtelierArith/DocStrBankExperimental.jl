solveaffine - 2Dポイントの2つのセット間のアフィン変換を解決します。

```
使用法: A = solveaffine(xy1, xy2)

引数:
   xy1, xy2 - 対応する2Dポイントの2xN配列

戻り値:
     A - xy2 = A*xy1となる3x3アフィン変換行列
         （xy1とxy2が同次座標系にあると仮定）

    [ x2        [ a  b  c    [ x1
      y2    =     d  e  f      y1
       1 ]        0  0  1 ]     1 ]

```
