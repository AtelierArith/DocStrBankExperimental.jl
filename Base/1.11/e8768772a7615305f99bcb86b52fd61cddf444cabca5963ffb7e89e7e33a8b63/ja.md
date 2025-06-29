```
permute!(v, p)
```

ベクトル `v` を、順列 `p` に従ってインプレースで並べ替えます。`p` が順列であることを確認するチェックは行われません。

新しい順列を返すには、`v[p]` を使用します。これは一般的に `permute!(v, p)` よりも速いです。事前に割り当てられた出力配列に書き込む場合は、`u .= @view v[p]` の方がさらに速いです。（`permute!` は `v` をインプレースで上書きしますが、内部的にはどの要素が移動されたかを追跡するためにいくつかの割り当てが必要です。）

!!! warning
    変更された引数が他の引数とメモリを共有している場合、動作が予期しないものになることがあります。


関連情報として [`invpermute!`](@ref) を参照してください。

# 例

```jldoctest
julia> A = [1, 1, 3, 4];

julia> perm = [2, 4, 3, 1];

julia> permute!(A, perm);

julia> A
4-element Vector{Int64}:
 1
 4
 3
 1
```
