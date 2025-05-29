```
fit(EarthModel, X, y; config::EarthConfig=EarthConfig(), prune=true, verbosity=0)
```

Friedmanの1991年のMARS手法（商標上の理由からEarthとも呼ばれる）に似たアプローチを使用して回帰モデルを適合させます。共変量は`X`にあり、ベクトル`y`には応答値が含まれています。

Earth/MARSは2つのステップから成ります：貪欲な基底構築と、無関係な項を排除することを目的とした剪定ステップです。基底関数はヒンジ関数の積です。この実装では、モデルを剪定するためにバックセレクションの代わりにLassoを使用します。

共変量`X`は、数値行列、データフレーム、ベクトルまたはベクトルのタプル、または値がベクトルである名前付きタプルであることができます。後者の2つの場合、各共変量ベクトルは数値型または文字列型である必要があり、またはCategoricalArrayのインスタンスである必要があります。後者の2つのタイプは、バイナリインジケータベクトルに展開されます。

`config`引数は、モデルの適合方法の多くの側面を指定するために使用できます。詳細については`EarthConfig`を参照してください。

参考文献：

Friedman (1991) "Multivariate Adaptive Regression Splines". Ann. Statist. 19(1): 1-67 (1991年3月). DOI: 10.1214/aos/1176347963 https://projecteuclid.org/journals/annals-of-statistics/volume-19/issue-1/Multivariate-Adaptive-Regression-Splines/10.1214/aos/1176347963.full

# キーワード引数

  * `weights`: オプションのケースウェイト
  * `config`: 多くのチューニングパラメータの設定を許可
  * `verbosity`: 適合アルゴリズムが実行される際にいくつかの情報を印刷
