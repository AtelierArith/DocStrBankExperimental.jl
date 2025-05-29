```
fload_All_Sync(fileLocation,fileName)
```

`fileLocation`に保存された`fileName`に格納されたすべてのデータを読み込みます。

# 例

```julia-repl
    (Run_Parameters,SAtot,SAtal,SMatrix,#=pMax,tMinMax,=#SConv) = fload_All_Sync(fileLocation,fileName);
```

ファイルに保存されたデータのタプルを返します。フィールドは次のとおりです：

  * `Run_Parameters` : 評価に使用されたパラメータのタプル。
  * `Stot` : すべてのシンクロトロン放射スペクトル値の合計を示す4D行列。
  * `Stal` : サンプリングされたシンクロトロン放射スペクトル値の数の集計を示す4D行列。
  * `SMatrix` : シンクロトロン放射スペクトルの4D行列。
  * `pMax` : 各ビンに対してサンプリングされた運動量空間変数p1（光子の運動量）の最大値。（数値拡散を修正するのに役立ちます）
  * `tMinMax` : 各ビンに対してサンプリングされた運動量空間変数t1の最小値と最大値。（数値拡散を修正するのに役立ちます）
  * `SConv` : 与えられた`Run_Parameters`での前回の実行と比較したシンクロトロン放射スペクトルの収束の4D行列。
