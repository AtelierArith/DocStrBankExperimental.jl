# リーマン・リウヴィル意味の導関数を三角ストリップ行列を用いて離散化し計算する。

```
fracdiff(f, α, end_point, h, RLDiffMatrix())
```

[三角ストリップ行列](https://en.wikipedia.org/wiki/Triangle_strip)を使用して分数導関数を近似します。

### 例

```julia-repl
julia> fracdiff(x->x^5, 0.5, 2.5, 0.0001, RLInt_Matrix())
```

!!! info
    三角ストリップ行列法は、区間 $[0, T]$ における導関数を `Vector` で返します。


```tex
@article{2009,
title={Matrix approach to discrete fractional calculus II: Partial fractional differential equations},
DOI={10.1016/j.jcp.2009.01.014},
author={Podlubny, Igor and Chechkin, Aleksei and Skovranek, Tomas and Chen, YangQuan and Vinagre Jara, Blas M.},
}
```
