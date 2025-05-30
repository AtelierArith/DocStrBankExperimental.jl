```
function LinearElasticityProblem(
    dimension::Int = 2;
    elasticity_modulus = 1.0,
    shear_modulus = 1.0,
    lambda = 1.0)
```

指定された次元の線形弾性問題のためのPDEDescriptionを作成します。

dimension == 1の場合、弾性*モジュラスのみがフックの剛性オペレーターのパラメータとして使用されます。dimension == 2の場合、せん断*モジュラスとラムダがフックの剛性オペレーターのラメパラメータとして使用されます。

境界および右辺データやその他の修正は、その後に追加する必要があります。
