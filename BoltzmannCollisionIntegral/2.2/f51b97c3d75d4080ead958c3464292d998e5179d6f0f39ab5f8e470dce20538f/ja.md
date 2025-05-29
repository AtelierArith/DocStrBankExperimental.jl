```
fload_Matrix(fileLocation,fileName)
```

`fileLocation`に保存された`fileName`に格納されたSおよびT行列のみを読み込みます。

# 例

```julia-repl
    Matrices = fload_All(fileLocation,fileName);
```

ファイルに保存されたデータのタプルを返します。フィールドは次のとおりです：

  * `Parameters` : 評価に使用されたパラメータのタプル。
  * `SMatrix3` : 12->34相互作用のための放出スペクトルの6D行列。
  * `SMatrix4` : 12->43相互作用のための放出スペクトルの6D行列。
  * `TMatrix1` : 12->34相互作用のための吸収スペクトルの4D行列。
  * `TMatrix2` : 21->34相互作用のための吸収スペクトルの4D行列。

初期粒子または最終粒子が同一の場合、その状態に対してはSMatricesまたはTMatricesのいずれか一方のみが返されます。
