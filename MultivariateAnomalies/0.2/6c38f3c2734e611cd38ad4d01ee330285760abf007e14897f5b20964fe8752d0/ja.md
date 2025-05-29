```
KNFST_train(K)
```

カーネル行列 `K` に基づいて、Paul Bodesheim、Alexander Freytag、Erik Rodner、Michael Kemmler、Joachim Denzlerによる「Kernel Null Space Methods for Novelty Detection」に従って、1クラスの新規性KNFSTモデルをトレーニングします。IEEE Conference on Computer Vision and Pattern Recognition (CVPR)、2013年の論文です。

# 出力

`(proj, targetValue)` `proj` 	– データポイントのための射影ベクトル（kx*projを介してxを射影します。ここで、kxはxとトレーニングデータのカーネル値を含む行ベクトルです） `targetValue` – null空間内のすべてのトレーニングサンプルの値
