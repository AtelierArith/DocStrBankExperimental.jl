```
==(G::SymmetricGroup, H::SymmetricGroup)
```

順列群が等しい場合は `true` を返し、そうでない場合は `false` を返します。

同じ数の文字の順列群であっても、異なる整数型でパラメータ化されている場合は異なるものと見なされます。

# 例

```
julia> G = SymmetricGroup(UInt(5))
5要素の順列群

julia> H = SymmetricGroup(5)
5要素の順列群

julia> G == H
false
```
