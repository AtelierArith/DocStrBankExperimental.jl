```
lyapunovspectrum([p::AbstractParticle,] bd::Billiard, t)
```

指定された粒子に対する有限時間リャプノフ指数（時間`t`で平均化）をビリヤードテーブルで返します。`t`は`Float`または`Int`のいずれかで、合計時間または衝突の合計回数を意味します。

ピン留めされた粒子にはゼロを返します。

粒子が指定されていない場合は、[`randominside`](@ref)を通じてランダムな粒子が選ばれます。並列化されたバージョンについては[`parallelize`](@ref)を参照してください。

[1] : Ch. Dellago *et al*, [Phys. Rev. E **53** (1996)](http://link.aps.org/doi/10.1103/PhysRevE.53.1485)
