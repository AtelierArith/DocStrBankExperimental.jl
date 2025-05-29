`catalan(W::ComplexReflectionGroup)`

は、不可約複素反射群 `W` のカタラン数を返します。良生成群の場合、この数は双対ブレイドモノイドのシンプルな要素の数に等しいです。他の群については、[Gordon and Griffeth2012](biblio.htm#gg12) によって定義されました。ウェイグル群の場合、これは根の反鎖の数もカウントします。

```julia-repl
julia> catalan(coxgroup(:A,7))
1430
```

`catalan(W,i)`

は、不可約複素反射群 `W` の `i` 番目のファス・カタラン数を返します。良生成群の場合、この数は双対モノイドにおけるシンプルな要素の鎖 `s₁,…,sᵢ` の数に等しく、ここで `sⱼ` は `sⱼ₊₁` を割ります。これらの群に対しては、`∏ⱼ(ih+dⱼ)/dⱼ` にも等しく、ここで積は `W` の反射次数にわたります。また、`h` は `W` のコクセター数です。非良生成群の場合、定義は [Gordon and Griffeth2012](biblio.htm#gg12) にあります。

```julia-repl
julia> catalan(complex_reflection_group(7),2)
16
```

`catalan(W;q=1)`、および `catalan(W,i;q=1)`

は、`q` が変数（`Pol()` や `Mvp` のような）である場合、`W` の `q`-カタラン数（および `i` 番目の `q`-ファス・カタラン数）を返します。再び、一般的な定義は [Gordon and Griffeth2012](biblio.htm#gg12) にあります。

```julia-repl
julia> catalan(complex_reflection_group(7),2;q=Pol())
Pol{Int64}: q⁷²+2q⁶⁰+3q⁴⁸+4q³⁶+3q²⁴+2q¹²+1
```
