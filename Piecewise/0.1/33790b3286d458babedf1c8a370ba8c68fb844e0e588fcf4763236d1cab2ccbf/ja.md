```
integraltransform(f::PiecewiseFunction, X::Any)
```

区分的関数 `f` の積分変換は次のように定義されます。

$$
(K\circ f)(\mathbf{X}) = \int_{-\infty}^{\infty}dx\,f(x)K(x,\mathbf{X}).
$$

このメソッドは、区分的関数 `f` で使用される各関数 `F(::Real, ::Vector{Any})` が、カーネル $K(x, \mathbf{X})$ に対する $F(x, \mathbf{a})$ の原始関数を返すメソッド `F(::Real, ::Vector{Any}, ::Any)` を持つことを前提としています。すなわち、`d/dx F(x, a, X) = F(x, a) * K(x, X)` です。もし `f.parity` が `:even` または `:odd` の場合、`integraltransform` は `d/dx F(1, x, a, X) = F(x, a) * (K(x, X) +  K(-x, X))` および `d/dx F(-1, x, a, X) = F(x, a) * (K(x, X) - K(-x, X))` を満たすメソッド `F(::Integer, ::Real, ::Vector{Any}, ::Any)` を要求します。

## 例

これは、任意の区分的線形関数を表すために使用できる `Formula` オブジェクト `LIN` を定義し、`integraltransform` がそのフーリエ変換を提供するようにします：

```julia-repl
julia> F(x, a) = a[1] + a[2] * x;
       LIN = Formula("LIN", 2, F, (a, s) -> a * s, a -> [a[1], -a[2]]);
       F(x, a, k) = (a[1] * k + a[2] * (k * x + im)) * exp(im * k * x)/(im * k^2);
       F(s, x, a, k) = 2 * (s == 1 ? real(F(x, a, k)) : im * imag(F(x, a, k)));
       f = PiecewiseFunction(:even, [Piece((0, π), LIN, [π, -1])])
< 区分的偶関数で、1つの部分とサポート [-3.1416, 3.1416] を持ちます >

julia> integraltransform(f, 1)
4.0
```
