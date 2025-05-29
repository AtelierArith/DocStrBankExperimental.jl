```
change_representer(M::ProbabilitySimplex, ::EuclideanMetric, p, X)
```

埋め込みからのメトリックに関する接ベクトルが与えられたとき、[`EuclideanMetric`](@extref `ManifoldsBase.EuclideanMetric`)における接空間上の線形関数の表現者は、$Z = p .* X .- p .* dot(p, X)$として適応されます。最初の部分は、[`ProbabilitySimplex`](@ref)上のリーマンメトリックにおける$p$による除算を「補償」し、2番目の部分はベクトルを接線に保つための適切な射影を行います。

詳細については、[AastroemPetraSchmitzerSchnoerr:2017](@cite)の命題2.3を参照してください。
