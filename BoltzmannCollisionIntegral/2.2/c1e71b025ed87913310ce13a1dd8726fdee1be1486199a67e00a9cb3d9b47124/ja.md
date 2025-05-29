```
fload_Matrix_ISO(fileLocation,fileName)
```

`fileLocation`に保存された`fileName`に格納されたS行列とT行列を読み込み、角度を合計することによって各行列を等方的な形に変換します。（行列の次元は同じままで、すなわち6D->6Dで、3つの次元のサイズは1になります）

# 例

```julia-repl
    Matrices = fload_All_ISO(fileLocation,fileName);
```

ファイルに保存されたデータのタプルを返します。フィールドは次のとおりです：

  * `Parameters` : 評価に使用されたパラメータのタプル。
  * `SMatrix3` : 12->34相互作用の放出スペクトルの6D行列。
  * `SMatrix4` : 12->43相互作用の放出スペクトルの6D行列。
  * `TMatrix1` : 12->34相互作用の吸収スペクトルの4D行列。
  * `TMatrix2` : 21->34相互作用の吸収スペクトルの4D行列。

初期または最終の粒子が同一である場合、その状態に対してはSMatricesまたはTMatricesのいずれか一方のみが返されます。
