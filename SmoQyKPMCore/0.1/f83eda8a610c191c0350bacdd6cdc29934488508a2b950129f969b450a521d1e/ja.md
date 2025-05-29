```
lanczos(niters, v, A, S = I, rng = Random.default_rng())
```

`niters` ランチョス反復を使用して、$A\cdot S$ の切り捨てられた三重対角行列の表現を、類似変換まで見つけます。ここで、$A$ は任意のエルミート行列であり、$S$ はエルミートかつ正定値です。従来のランチョスは単位行列 $S = I$ を使用します。非単位行列 $S$ への拡張は次のようになります：各行列ベクトル積 $A\cdot v$ は $(A S) \cdot v$ に、各ベクトル内積 $w^\dagger \cdot v$ は $w^\dagger \cdot S \cdot v$ になります。以下の実装はウィキペディアに従い、ペイジによって考慮された4つのバリアントの中で最も安定しています [1]。この実装は追加のベクトルストレージを導入し、各ランチョス反復がそれぞれ $A$ と $S$ に対して1回の行列ベクトル乗算のみを必要とします。

この関数は [`SymTridiagonal`](https://docs.julialang.org/en/v1/stdlib/LinearAlgebra/#LinearAlgebra.SymTridiagonal) 行列を返します。[`eigmin`](https://docs.julialang.org/en/v1/stdlib/LinearAlgebra/#LinearAlgebra.eigmin) および [`eigmax`](https://docs.julialang.org/en/v1/stdlib/LinearAlgebra/#LinearAlgebra.eigmax) ルーチンには [`SymTridiagonal`](https://docs.julialang.org/en/v1/stdlib/LinearAlgebra/#LinearAlgebra.SymTridiagonal) 行列型のための [特化した実装](https://docs.julialang.org/en/v1/stdlib/LinearAlgebra/#Elementary-operations) があります。

# ランチョスの類似の一般化は [2] および [3] で考慮されています。

# 

# 1. C. C. Paige, IMA J. Appl. Math., 373-381 (1972),

# https://doi.org/10.1093%2Fimamat%2F10.3.373.

# 2. H. A. van der Vorst, Math. Comp. 39, 559-561 (1982),

# https://doi.org/10.1090/s0025-5718-1982-0669648-0

# 3. M. Grüning, A. Marini, X. Gonze, Comput. Mater. Sci. 50, 2148-2156 (2011),

# https://doi.org/10.1016/j.commatsci.2011.02.021.
