```
bseries(avf::AverageVectorFieldMethod, order)
```

指定された整数 `order` までの [`AverageVectorFieldMethod`](@ref) の B-系列を計算します。

!!! note "基本微分による正規化"
    `bseries` によって返される B-系列の係数は、時間ステップのべき乗を根付き木の `symmetry` で割り、入力ベクトル場 $f$ の対応する基本微分で掛ける必要があります。詳細は [`evaluate`](@ref) を参照してください。

