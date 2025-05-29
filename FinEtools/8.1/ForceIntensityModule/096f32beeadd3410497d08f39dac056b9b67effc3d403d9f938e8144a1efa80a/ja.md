```
ForceIntensity(
    ::Type{T},
    ndofn,
    computeforce!::F,
) where {T<:Number, F<:Function}
```

関数が強度ベクトルを計算するために与えられたときに、力の強度を構築します。

# 引数

  * `T` = 力ベクトルの要素の型、通常は浮動小数点数または複素浮動小数点数、
  * `ndofn` = 力ベクトルの要素数（力ベクトルの長さ）、
  * `computeforce!` = コールバック関数。関数 `computeforce!` は次のシグネチャを持つ必要があります： `function computeforce!(forceout::Vector{CT}, XYZ::Matrix{T},       tangents::Matrix{T}, feid::IT) ) where {CT, T<:Number, IT<:Integer}       # 力を計算し、それをバッファ forceout にコピーします....       return forceout   end`   そして、現在の力を位置 `XYZ` でバッファ `forceout` に記入する必要があります。必要に応じて、ヤコビ行列 `tangents` に提供された情報と有限要素の識別子 `feid` を使用します。
