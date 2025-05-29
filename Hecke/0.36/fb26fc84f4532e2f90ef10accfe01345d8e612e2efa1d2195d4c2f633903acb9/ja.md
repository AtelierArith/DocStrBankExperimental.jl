```
torsion_quadratic_module(M::ZZLat, N::ZZLat; gens::Union{Nothing, Vector{<:Vector}} = nothing,
                                             snf::Bool = true,
                                             modulus::RationalUnion = QQFieldElem(0),
                                             modulus_qf::RationalUnion = QQFieldElem(0),
                                             check::Bool = true) -> TorQuadModule
```

Z-ラティス $M$ と $M$ の部分ラティス $N$ が与えられたとき、トーション二次モジュール $M/N$ を返します。

`gens` が設定されている場合、`gens` の画像がアーベル群 $M/N$ の生成元として使用されます。

`snf` が `true` の場合、基礎となるアーベル群はスミス正規形になります。そうでない場合、$M$ の基底の画像が生成元として使用されます。

関連する有限双線形および二次形式のモジュラスは、それぞれ `modulus` と `modulus_qf` に希望の値を設定することで決定できます。
