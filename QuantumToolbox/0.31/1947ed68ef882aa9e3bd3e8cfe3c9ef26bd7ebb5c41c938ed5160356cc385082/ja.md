```
coherent(N::Int, α::Number)
```

生成された[コヒーレント状態](https://en.wikipedia.org/wiki/Coherent_state) $|\alpha\rangle$は、ボソニック消滅演算子の固有ベクトルとして定義されます $\hat{a} |\alpha\rangle = \alpha |\alpha\rangle$。

この状態は、変位演算子[`displace`](@ref)とゼロフォック状態[`fock`](@ref)を介して構築されます: $|\alpha\rangle = \hat{D}(\alpha) |0\rangle$
