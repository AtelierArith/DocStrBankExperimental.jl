```
ValueAccessor{S<:AbstractValueShape}
```

値アクセサは、指定されたオフセット位置に格納されたフラットな実数値データベクター内の指定された形状の値にアクセスする手段を提供します。

コンストラクタ:

```
ValueAccessor{S}(shape::S, offset::Int)
```

オフセットはフラットデータ配列の最初のインデックスに対して相対的であるため、値が配列の先頭に格納されている場合、オフセットはゼロになります。

`ValueAccessor`は、指定されたフラットデータ配列にインデックスを付けるために使用できます。

例:

```julia
acc = ValueAccessor(ArrayShape{Real}(2,3), 2)
valshape(acc) == ArrayShape{Real,2}((2, 3))
data = [1, 2, 3, 4, 5, 6, 7, 8, 9]
data[acc] == acc(data) == [3 5 7; 4 6 8]
```

注意: [`AbstractValueShape`](@ref) のサブタイプは、それらの `ValueAccessor{...}` のために [`ValueShapes.vs_getindex`](@ref)、[`ValueShapes.vs_unsafe_view`](@ref) および [`ValueShapes.vs_setindex!`](@ref) を特化させるべきです。`Base.getindex`、`Base.view`、`Base.unsafe_view` または `Base.setindex!` を直接特化させると、これらの関数を非常に一般的な方法で特化させるカスタム配列テープとのメソッドの曖昧さが生じる可能性があります。
