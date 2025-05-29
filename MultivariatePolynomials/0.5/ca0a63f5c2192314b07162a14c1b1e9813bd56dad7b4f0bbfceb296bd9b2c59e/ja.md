```
antidifferentiate(p::AbstractPolynomialLike, v::AbstractVariable, deg::Union{Int, Val}=1)
```

変数 `v` に対して多項式 `p` を `deg` 回反微分します。反微分に関与する自由定数は 0 に設定されます。

```
antidifferentiate(p::AbstractPolynomialLike, vs, deg::Union{Int, Val}=1)
```

変数のベクトルまたはタプル `vs` に対して多項式 `p` を `deg` 回反微分し、次元 `deg` の配列を返します。コンパイル時に次数が既知の場合は、`antidifferentiate(p, v, Val{2}())` のように `Val` インスタンスとして `deg` を渡すことをお勧めします。これにより、コンパイラが戻り値の型を推論するのに役立ちます。

### 例

```julia
p = 3x^2*y + x + 2y + 1
antidifferentiate(p, x) # は 3x^3* + 1/2*x + 2xy + x を返すべきです
antidifferentiate(p, x, Val{1}()) # 上記と同等
antidifferentiate(p, (x, y)) # は [3x^3* + 1/2*x + 2xy + x, 3/2x^2*y^2 + xy + y^2 + y] を返すべきです
```
