```
ColVecs(X::AbstractMatrix)
```

`AbstractMatrix`の軽量ラッパーで、これをベクトルのベクトルとして解釈し、`X`の各*列*が単一のベクトルを表します。

つまり、`x = ColVecs(X)`と書くことで、"`x`はベクトルのベクトルであり、それぞれの長さは`size(X, 1)`です。ベクトルの総数は`size(X, 2)`です。"と言っていることになります。

言い換えれば、`ColVecs(X)`は`X`を水平方向に連結された列ベクトルのベクトルとして解釈すべきであることを示しており、これが`ColVecs`という名前の由来です。

```jldoctest
julia> X = randn(2, 5);

julia> x = ColVecs(X);

julia> length(x) == 5
true

julia> X[:, 3] == x[3]
true
```

`ColVecs`は転置を介して[`RowVecs`](@ref)に関連しています：

```jldoctest
julia> X = randn(2, 5);

julia> ColVecs(X) == RowVecs(X')
true
```
