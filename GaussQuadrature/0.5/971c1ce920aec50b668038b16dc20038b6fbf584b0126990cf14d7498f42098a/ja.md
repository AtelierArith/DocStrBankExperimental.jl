```
x, w = custom_gauss_rule(lo, hi, a, b, endpt, maxits=maxiterations[T])
```

重み関数 `w(x)` を持つガウスルールのための点 `x` と重み `w` を生成します。区間 `lo < x < hi` で。

配列 `a` と `b` は、単項直交多項式 `p(0,x)`, `p(1,x)`, `p(2,x)`, ... の三項再帰関係における係数（例えば `legendre_coeff` によって与えられる）を保持しています。すなわち、

```
p(k, x) = (x-a[k]) p(k-1, x) - b[k]² p(k-2, x),    k ≥ 1,
```

ここで `p(0, x) = 1` であり、慣例として `p(-1, x) = 0` で、

```
          hi
b[1]^2 = ∫  w(x) dx.
         lo
```

したがって、`p(k, x) = xᵏ + 低次の項` であり、

```
 hi
∫  p(j, x) p(k, x) w(x) dx = 0 if j ≠ k.
lo
```
