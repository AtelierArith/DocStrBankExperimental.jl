```
Recursive{Side,T} <: RewritingOrdering
Recursive{Side}(A::Alphabet; order=collect(A))
```

各文字に一意のレベルが与えられる`WreathOrder`の特別なケースです。

レベルが一意であるため、アルファベット`A`の文字を線形に順序付けます。この順序は一般的に小さい生成子を促進し、大きい生成子は最小の単語の中で比較的早く現れます。例えば、`a < b`であれば、`a·b > b·aⁿ`となります。

# 定義

アルファベット`A`上の部分順序`(A, <)`が与えられたとき、`p, q ∈ A*`に対して、左再帰的順序に関して`p < q`であると言います。

> 1. `p == ε ≠ q`、または
> 2. `p = p′·a`、`q = q′·b`であり、ここで`a, b ∈ A`であるとき
>
>       * `a == b`かつ`p′ < q′`、または
>       * `a < b`かつ`p < q′`、または
>       * `a > b`かつ`p′ < q`


右再帰的順序の場合、ポイント2の分解を次のように変更する必要があります。

> `p = a·p′`、`q = b·q′`であり、ここで`a, b ∈ A`…


詳細については、次を参照してください。

> M. Jentzen *Confluent String Rewriting*, 定義 1.2.14 p.24。


この順序は時々*再帰的パス順序*としても知られ、例えば多巡回群にとって有用です。

# 例

```jldoctest
julia> X = Alphabet([:b, :a, :A],[0, 3, 2]);

julia> b, a, A = [Word([i]) for i in 1:length(X)];

julia> rec = Recursive(X, order=[:a, :A, :b])
KnuthBendix.Left-Recursive: a < A < b

julia> lt(rec, b*a^10, a*b)
true

julia> lt(rec, b*a^10, b)
false

julia> lt(rec, a*A, b*a^10)
true

julia> rt_rec = Recursive{KnuthBendix.Right}(X, order=[:a, :A, :b])
KnuthBendix.Right-Recursive: a < A < b
```
