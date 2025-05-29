```
RowVecs(X::AbstractMatrix)
```

`AbstractMatrix`の軽量ラッパーで、これをベクトルのベクトルとして解釈し、`X`の各*行*が単一のベクトルを表します。

つまり、`x = RowVecs(X)`と書くことで、"`x`はベクトルのベクトルであり、それぞれの長さは`size(X, 2)`です。ベクトルの総数は`size(X, 1)`です。"と言っていることになります。

別の言い方をすると、`RowVecs(X)`は`X`を縦に連結された行ベクトルのベクトルとして解釈すべきであることを示しており、これが`RowVecs`という名前の由来です。

内部的には、データは引き続き`AbstractMatrix`として表現されるため、この型を使用してもパフォーマンスのペナルティは発生しません。

```jldoctest
julia> X = randn(5, 2);

julia> x = RowVecs(X);

julia> length(x) == 5
true

julia> X[3, :] == x[3]
true
```

`RowVecs`は転置を介して[`ColVecs`](@ref)に関連しています：

```jldoctest
julia> X = randn(5, 2);

julia> RowVecs(X) == ColVecs(X')
true
```
