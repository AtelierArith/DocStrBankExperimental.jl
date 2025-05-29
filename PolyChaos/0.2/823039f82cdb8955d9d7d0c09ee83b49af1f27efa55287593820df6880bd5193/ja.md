**単変量**

```
computeSP(a::AbstractVector{<:Integer},α::AbstractVector{<:Real},β::AbstractVector{<:Real},nodes::AbstractVector{<:Real},weights::AbstractVector{<:Real};issymmetric::Bool=false)
computeSP(a::AbstractVector{<:Integer},op::AbstractOrthoPoly;issymmetric=issymmetric(op))
```

**多変量**

```
computeSP( a::AbstractVector{<:Integer},
           α::AbstractVector{<:AbstractVector{<:Real}},β::AbstractVector{<:AbstractVector{<:Real}},
           nodes::AbstractVector{<:AbstractVector{<:Real}},weights::AbstractVector{<:AbstractVector{<:Real}},
           ind::AbstractMatrix{<:Integer};
           issymmetric::BitArray=falses(length(α)))
computeSP(a::AbstractVector{<:Integer},op::AbstractVector,ind::AbstractMatrix{<:Integer})
computeSP(a::AbstractVector{<:Integer},mOP::MultiOrthoPoly)
```

スカラー積を計算します

$$
\langle \phi_{a_1},\phi_{a_2},\cdots,\phi_{a_n} \rangle,
$$

ここで `n = length(a)` です。これは再帰係数 `(α,β)` と数値積分ルール `(nodes,weights)`、さらに多重インデックス `ind` を提供する必要があります。キーワード `issymmetric` を介して提供された場合、重み関数の対称性が利用されます。多変量スカラー積のすべての計算は、単変量スカラー積の効率的な計算に戻ります。数学的には、これはフビニの定理に従います。

この関数は `AbstractOrthoPoly` とその数値積分ルール `Quad` との使用を容易にするためにディスパッチされます。

!!! note
      * $$
        a
        $$

        のゼロエントリは、自動的に削除され、計算が簡素化されます。これは以下に従います

    $$
    \langle \phi_i, \phi_j, \phi_0,\cdots,\phi_0 \rangle = \langle \phi_i, \phi_j \rangle,
    $$

    これは `\phi_0 = 1` であるためです。

      * 積分を正確に解くために十分な数値積分点が供給されているかどうかがチェックされます。

