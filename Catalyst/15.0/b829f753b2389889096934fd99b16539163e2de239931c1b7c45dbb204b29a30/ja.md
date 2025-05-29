```
iscomplexbalanced(rs::ReactionSystem, parametermap; sparse = false)
```

ネットワークが複雑平衡の平衡解を持つかどうかを、van der Schaft et al. の方法に従って構成的に計算します。[2015](https://link.springer.com/article/10.1007/s10910-015-0498-2#Sec3)。

パラメータ/反応速度定数の値を指定する必要があります。パラメータと値のマッピングの辞書、ベクトル、またはタプルを受け入れます。例: [k1 => 1.0, k2 => 2.0,...]。
