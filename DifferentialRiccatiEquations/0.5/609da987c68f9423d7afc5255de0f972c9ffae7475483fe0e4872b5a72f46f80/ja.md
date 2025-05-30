```
compress!(X::LDLᵀ)
```

内部コンポーネントを連結し、[^\Lang2015]に従って列圧縮を行います。

これは高コストの操作です。

関連情報: [`concatenate!`](@ref), [`orthf`](@ref)

[^Lang2015]: N Lang, H Mena, and J Saak, "On the benefits of the LDLT factorization for large-scale differential matrix equation solvers" Linear Algebra and its Applications 480 (2015): 44-71. [doi:10.1016/j.laa.2015.04.006](https://doi.org/10.1016/j.laa.2015.04.006)
