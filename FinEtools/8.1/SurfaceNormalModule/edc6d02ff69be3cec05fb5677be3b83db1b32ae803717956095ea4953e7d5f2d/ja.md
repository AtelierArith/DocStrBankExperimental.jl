```
SurfaceNormal(ndimensions, z::T, computenormal!::F) where {T<:Number, F<:Function}
```

法線ベクトルを計算する関数が与えられたときに、表面法線評価器を構築します。

# 引数

  * `T` = 法線ベクトルの要素の型、
  * `ndofn` = 法線ベクトルの成分の数、
  * `computenormal!` = コールバック関数。関数 `computenormal!` は次のシグネチャを持つ必要があります。

    `function computenormal!(normalout::Vector{CT}, XYZ::AbstractVecOrMat{<:Real},       tangents::AbstractMatrix{<:Real}, feid::IT, qpid::IT) where {CT, IT}       # 法線を計算し、バッファにコピーします....       return normalout   end`

    そして、必要に応じて、ヤコビ行列 `tangents` に提供された情報、有限要素の識別子 `feid`、および数値点ID `qpid` を使用して、位置 `XYZ` での現在の法線をバッファ `normalout` に記入する必要があります。 [`DataCache`](@ref) を参照してください。
