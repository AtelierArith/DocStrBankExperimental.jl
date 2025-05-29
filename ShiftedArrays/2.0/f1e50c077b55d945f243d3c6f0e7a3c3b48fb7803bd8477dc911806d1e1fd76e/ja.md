```
ShiftedArray(parent::AbstractArray, shifts, default)
```

`AbstractArray`オブジェクトをカスタムで作成し、`shifts`ステップだけシフトされた`AbstractArray` `parent`を格納します（ここで`shifts`は`parent`の次元ごとに1つの`shift`値を持つ`Tuple`です）。`s::ShiftedArray`に対して、`s[i...] == s.parent[map(-, i, s.shifts)...]`が成り立つ場合、`map(-, i, s.shifts)`が`s.parent`の有効なインデックスであり、そうでない場合は`s.v[i, ...] == default`となります。`ShiftedArray`の値を通常の`Array`に収集するには`copy`を使用します。推奨されるコンストラクタは`ShiftedArray(parent, shifts; default = missing)`です。

!!! note
    `parent`が互換性のあるデフォルト値を持つ`ShiftedArray`である場合、コンストラクタは`ShiftedArray`オブジェクトをネストするのではなく、シフトを加算的に結合します。


# 例

```jldoctest shiftedarray
julia> v = [1, 3, 5, 4];

julia> s = ShiftedArray(v, (1,))
4-element ShiftedVector{Int64, Missing, Vector{Int64}}:
  missing
 1
 3
 5

julia> v = [1, 3, 5, 4];

julia> s = ShiftedArray(v, (1,))
4-element ShiftedVector{Int64, Missing, Vector{Int64}}:
  missing
 1
 3
 5

julia> copy(s)
4-element Vector{Union{Missing, Int64}}:
  missing
 1
 3
 5

julia> v = reshape(1:16, 4, 4);

julia> s = ShiftedArray(v, (0, 2))
4×4 ShiftedArray{Int64, Missing, 2, Base.ReshapedArray{Int64, 2, UnitRange{Int64}, Tuple{}}}:
 missing  missing  1  5
 missing  missing  2  6
 missing  missing  3  7
 missing  missing  4  8

julia> shifts(s)
(0, 2)
```
