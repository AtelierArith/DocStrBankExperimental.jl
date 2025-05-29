```
DirichletProcessPartitionDistribution(k::Integer, α::Float64)
DirichletProcessPartitionDistribution(k::Integer, s::Symbol)
DirichletProcessPartitionDistribution(k::Integer, α::Real)
```

パーティションに対するディリクレ過程分布。浮動小数点数を渡すことで直接αを設定するか、事前に指定されたオプションのためにシンボルを渡します。`:Gopalan_Berry`は`EqualitySampler.dpp_find_α`を使用してαを指定し、Gopalan & Berry (1998)によるヒューリスティックを使用して、P(すべて等しい) == P(すべて異なる)となるようにします。`harmonic`はαをk番目の調和数の逆数に設定し、これによりパーティションに対する事前分布が減少することを意味します。
