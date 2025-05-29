```
location{D<:AbstractMvLogNormal}(::Type{D},s::Symbol,m::AbstractVector,S::AbstractMatrix)
```

位置ベクトル（基になる正規分布の平均）を計算します。

  * `s == :meancov` の場合、mは平均として取り扱われ、Sは対数正規分布の共分散行列として取り扱われます。
  * `s == :mean | :median | :mode` の場合、mはそれぞれ対数正規分布の平均、中央値、またはモードとして取り扱われ、Sはスケール行列（基になる正規分布の共分散）として解釈されます。

中央値 + 共分散やモード + 共分散から位置ベクトルを解析的に計算することはできません。
