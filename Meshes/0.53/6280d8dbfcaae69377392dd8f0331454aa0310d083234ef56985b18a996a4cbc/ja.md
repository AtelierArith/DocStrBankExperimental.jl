```
laplacematrix(mesh; kind=nothing)
```

`mesh`のラプラス-ベルトラミ（別名ラプラシアン）行列。オプションで、離散化の`kind`を指定します。

## 利用可能な離散化

  * `:uniform`   - `Lᵢⱼ = 1 / |𝒜(i)|, ∀j ∈ 𝒜(i)`
  * `:cotangent` - `Lᵢⱼ = cot(αᵢⱼ) + cot(βᵢⱼ), ∀j ∈ 𝒜(i)`

ここで、`𝒜(i)`は頂点`i`の隣接関係です。

## 参考文献

  * Botsch et al. 2010. [Polygon Mesh Processing](http://www.pmp-book.org).
  * Pinkall, U. & Polthier, K. 1993. [Computing discrete minimal surfaces and their conjugates](https://projecteuclid.org/journals/experimental-mathematics/volume-2/issue-1/Computing-discrete-minimal-surfaces-and-their-conjugates/em/1062620735.full).
