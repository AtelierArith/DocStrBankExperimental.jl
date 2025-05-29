```
hom(R::AbstractAlgebra.PolyRing, S::NCRing, [coeff_map,] image)
```

与えられた同型写像 `coeff_map` が `C` から `S` へのものであり、ここで `C` は `R` の係数環であり、与えられた要素 `image` は `S` のものであるとき、`R` から `S` への同型写像を返します。この同型写像は `C` に対して `coeff_map` に制限され、`R` の生成元を `image` に送ります。

係数写像が入力されていない場合、`C` から `S` への標準的な同型写像を呼び出します。もしそのような同型写像が存在しない場合はエラーを投げます。

# 例

```jldoctest
julia> Zx, x = ZZ[:x];

julia> F = hom(Zx, Zx, x + 1);

julia> F(x^2)
x^2 + 2*x + 1

julia> Fp = GF(3); Fpy, y = Fp[:y];

julia> G = hom(Zx, Fpy, c -> Fp(c), y^3);

julia> G(5*x + 1)
2*y^3 + 1
```
