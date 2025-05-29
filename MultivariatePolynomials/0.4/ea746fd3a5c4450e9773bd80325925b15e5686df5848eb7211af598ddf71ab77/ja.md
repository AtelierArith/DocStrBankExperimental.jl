```
differentiate(p::AbstractPolynomialLike, v::AbstractVariable, deg::Union{Int, Val}=1)
```

変数 `v` に対して多項式 `p` を `deg` 回微分します。

```
differentiate(p::AbstractPolynomialLike, vs, deg::Union{Int, Val}=1)
```

変数のベクトルまたはタプル `vs` に対して多項式 `p` を `deg` 回微分し、次元 `deg` の配列を返します。コンパイル時に次数が既知の場合は、`differentiate(p, v, Val{2}())` のように `Val` インスタンスとして `deg` を渡すことをお勧めします。これにより、コンパイラが戻り値の型を推論しやすくなります。

```
differentiate(p::AbstractArray{<:AbstractPolynomialLike, N}, vs, deg::Union{Int, Val}=1) where N
```

ベクトルまたはタプルの変数 `vs` に対して `p` の多項式を微分し、次元 `N+deg` の配列を返します。`p` が `AbstractVector` の場合、これは `p` のヤコビ行列を返し、i 番目の行には `p[i]` の偏微分が含まれます。

### 例

```julia
p = 3x^2*y + x + 2y + 1
differentiate(p, x) # は 6xy + 1 を返すべき
differentiate(p, x, Val{1}()) # 上記と同等
differentiate(p, (x, y)) # は [6xy+1, 3x^2+1] を返すべき
differentiate( [x^2+y, z^2+4x], [x, y, z]) # は [2x 1 0; 4 0 2z] を返すべき
```
