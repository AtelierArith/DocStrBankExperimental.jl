```
kernelproduct(rule::NeighborhoodRule})
kernelproduct(hood::AbstractKernelNeighborhood)
kernelproduct(hood::Neighborhood, kernel)
```

近傍とカーネルのベクトルドット積を返しますが、`dot`とは異なり、近傍のベクトルメンバーに対してドット積は取られず、それらはスカラーとして扱われます。
