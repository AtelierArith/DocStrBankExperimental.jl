```
push(collection, items...)
```

`collection`のすべての要素と`items`のすべての要素を含む新しいコレクションを返します。

# 例

```jldoctest
julia> s = DigitSet([4, 9]);

julia> push(s, 1, 11)
DigitSet with 4 elements:
  1
  4
  9
  11
```
