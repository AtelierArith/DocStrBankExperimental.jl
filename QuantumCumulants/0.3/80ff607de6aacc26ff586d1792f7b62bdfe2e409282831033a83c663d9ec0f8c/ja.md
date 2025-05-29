```
subst_reds(de::AbstractMeanfieldEquations)
```

与えられた方程式内の可能な冗長共役平均を、左辺の平均の1つの共役として与えられた対応する平均に置き換える関数です。

# オプション引数

*`scaling`: 平均が`missed`ベクターに追加される方法を定義するBool。trueの場合、演算子（インデックスなし）がすでに`missed`ベクター内にない平均のみが追加されます。
