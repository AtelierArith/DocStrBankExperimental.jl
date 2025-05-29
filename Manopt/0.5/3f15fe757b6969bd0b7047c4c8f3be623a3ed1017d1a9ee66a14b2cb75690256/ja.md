```
AbstractVectorFunction{E, FT} <: Function
```

抽象ベクトル関数 $f:\mathcal M → ℝ^n$ を [`AbstractEvaluationType`](@ref) `E` と、$f$ が実装される形式を指定するための [`AbstractVectorialType`](@ref) で表します。

# $f$ の表現

$$
f
$$

の表現は3つあり、状況に応じて有益である可能性があります：

  * 単一の関数 $f$ を格納する [`FunctionVectorialType`](@ref) で、ベクトルを返します。
  * 各々が単一の値を返す関数 $f_i$ のベクトルを格納する [`ComponentVectorialType`](@ref) で、
  * 勾配とヘッセ行列のための接空間の特定の基底に関して関数を格納する [`CoordinateVectorialType`](@ref) です。このタイプの勾配は通常、ヤコビアンと呼ばれます。

[`ComponentVectorialType`](@ref) については、$f$ がその成分関数を用いても書けることを想像してください、

$$
f(p) = \bigl( f_1(p), f_2(p), \ldots, f_n(p) \bigr)^{\mathrm{T}}
$$

この表現では、`f` はその成分関数のベクトル `[f1(M,p), f2(M,p), ..., fn(M,p)]` として与えられます。利点は、個々の成分を評価でき、この表現からは数 $n$ を直接読み取ることができる点です。欠点は、多くの個別の（成分）関数を実装しなければならないことかもしれません。

[`FunctionVectorialType`](@ref) では、$f$ は単一の関数 `f(M, p)` として実装され、`AbstractArray` を返します。ここでの利点は、これは単一の関数であることです。欠点は、たとえ単一の成分を計算するのが高価であっても、すべての `f` を評価しなければならないことかもしれません。
