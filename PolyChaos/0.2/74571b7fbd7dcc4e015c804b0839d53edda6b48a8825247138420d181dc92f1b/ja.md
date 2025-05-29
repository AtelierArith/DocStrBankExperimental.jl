```
mcdiscretization(N::Int,quads::Vector{},discretemeasure::AbstractMatrix{<:Real}=zeros(0,2);discretization::Function=stieltjes,Nmax::Integer=300,ε::Float64=1e-8,gaussquad::Bool=false)
```

このルーチンは、$N$ 個の再帰係数を返します。これらの係数は、$m$ 個の重み $w_i$ の合計として分解された重み関数 $w$ に対して直交する多項式に関連しています。重みの定義域は $[a_i,b_i]$ であり、$i=1,\dots,m$ の範囲です。

$$
w(t) = \sum_{i}^{m} w_i(t) \quad \text{with } \operatorname{dom}(w_i) = [a_i, b_i].
$$

各重み $w_i$ とその定義域 $[a_i, b_i]$ に対して、関数 `mcdiscretization()` は次の形式の数値積分ルールを期待します：nodes::AbstractVector{<:Real}, weights::AbstractVector{<:Real} = my*quad*i(N::Int)。これらはすべてパラメータ `quad` にスタックされます。quad = [ my*quad*1, ..., my*quad*m ] 重み関数に離散部分がある場合（`discretemeasure` で指定）、それは離散化された連続重み関数に追加されます。

関数 `mcdiscretization()` は、与えられた重み $w(t)$ の一連の離散化を実行します。各離散化は、目的の再帰係数の近似を生成するために、Stieltjes または Lanczos 手法（キーワード `discretization in [stieltjes, lanczos]`）の適用に続きます。関数は、各サブ区間 $i$ に対して `N` 点の数値積分ルール（`quad` の $i$ 番目のエントリ）を適用して、そのサブ区間上の重み関数 $w_i$ を離散化します。手続きが所定の精度 `ε` に収束する前に、`N` が最大許容値 `Nmax` に達する場合があります。関数が収束しない場合、エラーメッセージが表示されます。

キーワード `gaussquad` は、すべての $m$ 重み $w_i(t)$ に対してガウス数値積分ルールが利用可能な場合に `true` に設定する必要があります（$i = 1, \dots, m$）。

詳細については、W. Gautschi "Orthogonal Polynomials: Approximation and Computation" のセクション 2.2.4 を参照してください。
