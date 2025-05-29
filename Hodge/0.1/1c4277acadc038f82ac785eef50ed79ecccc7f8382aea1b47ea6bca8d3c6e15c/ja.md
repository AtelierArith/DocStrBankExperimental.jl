```
Cochain{R, n}
```

リング `R` 上のコチェインの `n` 番目の群 $C^n(K; R)$ を、基底空間が単体複体 `K` であるものとして表します。

コチェインを構築する方法については、[`zero_cochain`](@ref) および [`indicator_cochain`](@ref) メソッドも参照してください。

この型の要素は、`K` の n-単体から `R` への関数として、または `K` の頂点上の斜対称 n-テンソルとして見ることができます。この第二の視点は、次の論文のアイデアに基づいています：

  * Jiang, X., Lim, L., Yao, Y. et al. Statistical ranking and combinatorial Hodge theory. Math. Program. 127, 203–244 (2011). https://doi.org/10.1007/s10107-010-0419-x
