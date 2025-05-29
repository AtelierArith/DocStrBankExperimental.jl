```
Disk{T,z₀,r}
```

半径`r`と中心`z₀`を持つ円盤を、境界を除いた集合`T`の中で表します。`r`は非負である必要があります。`z`と`r`の両方は有限であり、NaNであってはいけません。

この型は、`@quickcheck`マクロのために、(abs(x-z) < r)を満たす型`T`の変数`x`を生成するために使用されます：

```
julia> @quickcheck (typeof(x) == ComplexF16 && abs(x-2im) < 3) (x :: Disk{Complex{Float16}, 2im, 3})
true
```
