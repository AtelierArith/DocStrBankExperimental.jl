```
MutableShiftedArray(parent::AbstractArray, shifts = (), viewsize=size(v); default = zero(eltype(parent)))
```

`AbstractArray`オブジェクトをカスタムで作成し、`shifts`ステップだけシフトされた`AbstractArray` `parent`を格納します（`shifts`は`parent`の各次元ごとに1つの`shift`値を持つ`Tuple`です）。`ShiftedArrays.jl`ツールボックスの`ShiftedArray`とは異なり、このオブジェクトは可変であり、パディングされた範囲での変更操作は無視されます。さらに、ビューのサイズ変更もサポートしています。

`s::MutableShiftedArray`に対して、`s[i...] == s.parent[map(-, i, s.shifts)...]`が成り立つのは、`map(-, i, s.shifts)`が`s.parent`の有効なインデックスである場合であり、そうでない場合は`s.v[i, ...] == default`となります。`MutableShiftedArray`の値を通常の`Array`に収集するには`copy`を使用します。推奨されるコンストラクタは`MutableShiftedArray(parent, shifts; default = missing)`です。

!!! note
    `parent`が互換性のあるデフォルト値を持つ`MutableShiftedArray`である場合、コンストラクタは`MutableShiftedArray`オブジェクトをネストするのではなく、シフトを加算的に結合します。


# 引数

  * `parent::AbstractArray`: シフトされる配列
  * `shifts::Tuple{Int}`: 各次元で`parent`がシフトされる量。デフォルトは空のTupleで、シフトは行われません。
  * `viewsize::Tuple{Int}`: ビューのサイズ。デフォルトでは親配列のサイズが使用されます。
  * `default::M`: 元の配列の範囲外のときに返されるデフォルト値。デフォルトでは対応する`eltype`のゼロが使用されます。デフォルト値に`missing`を使用すると、Union型のためにCUDAでの単一インデックスアクセスが発生することに注意してください。

# 例

```jldoctest shiftedarray
julia> v = [1, 3, 5, 4];

julia> s = MutableShiftedArray(v, (1,))
4-element MutableShiftedVector{Int64, Int64, Vector{Int64}}:
 0
 1
 3
 5

julia> copy(s)
4-element Vector{Int64}:
 0
 1
 3
 5

julia> v = reshape(1:16, 4, 4);

julia> s = MutableShiftedArray(v, (0, 2), default=missing)
4×4 MutableShiftedArray{Int64, Missing, 2, Base.ReshapedArray{Int64, 2, UnitRange{Int64}, Tuple{}}}:
 missing  missing  1  5
 missing  missing  2  6
 missing  missing  3  7
 missing  missing  4  8

julia> shifts(s)
(0, 2)
```
