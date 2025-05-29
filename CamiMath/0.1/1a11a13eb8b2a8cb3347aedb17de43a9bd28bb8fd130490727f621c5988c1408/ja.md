```
faulhaber_polynomial(n::Integer, p::Int [; msg=true])
```

次数 `p` のファウルハーバーポリノミアル 

$$
    F(n,p)=\sum_{j=0}^{p}c_{j}n^{j},
$$

ここで `n` は正の整数で、係数はベクトル $c=[c_0,⋯\ c_p]$ に含まれ、[`faulhaber_polynom`](@ref) によって与えられます。

  * `msg` : 整数オーバーフロー保護 (IOP) - 有効化時の警告

#### 例:

```
julia> faulhaber_polynomial(3, 6)
276

julia> faulhaber_polynomial(5, 30)
IOP capture: faulhaber_polynomial(5, 30) autoconverted to Rational{BigInt}
186552813930161650665
```
