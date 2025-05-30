```
reinterpret(T::DataType, A::AbstractArray)
```

与えられた配列と同じバイナリデータを持つ配列のビューを、要素型を `T` として構築します。

この関数は、要素が明示的に取得されるまで計算されない「遅延」配列にも適用できます。たとえば、範囲 `1:6` に対する `reinterpret` は、密なベクトル `collect(1:6)` に対するものと同様に動作します：

```jldoctest
julia> reinterpret(Float32, UInt32[1 2 3 4 5])
1×5 reinterpret(Float32, ::Matrix{UInt32}):
 1.0f-45  3.0f-45  4.0f-45  6.0f-45  7.0f-45

julia> reinterpret(Complex{Int}, 1:6)
3-element reinterpret(Complex{Int64}, ::UnitRange{Int64}):
 1 + 2im
 3 + 4im
 5 + 6im
```
