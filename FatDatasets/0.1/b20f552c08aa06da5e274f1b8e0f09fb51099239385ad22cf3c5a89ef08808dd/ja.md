```julia
RandomStreamDataset(T, d, n, f)
RandomStreamDataset(T, d, n, f, rng)

```

固定されたシードを持つため、複数回反復できるように、ランダムに生成され、即座に利用可能なデータセットです。`BatchIterators`パッケージの`BatchIterator`を使用して`RandomStreamDataset`を反復することが可能です。パラメータ`f`は、パラメータ(i::Int, rng::MersenneTwister)に対して、型`T`の要素からなる`d`×`i`行列を返す関数である必要があります。乱数生成器は順次使用されるべきであり、したがってf(2,rng)はf(1,rng)への2回の呼び出しの結果を連結したものと同じである必要があります。
