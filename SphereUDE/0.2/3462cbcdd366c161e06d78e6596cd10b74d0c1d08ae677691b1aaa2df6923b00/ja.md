三次元単位ベクトルの行列にフィッシャー雑音を追加する

これは、型FisherNoise <: AbstractNoiseの定義によって行われ、基本定義の+(,)を拡張してシンプルな構文を可能にします。

X*noise = X*noiseless + FisherNoise(kappa=200.)
