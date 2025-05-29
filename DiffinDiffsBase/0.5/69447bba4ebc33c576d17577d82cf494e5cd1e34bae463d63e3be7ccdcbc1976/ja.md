```
RotatingTimeArray{T<:RotatingTimeValue,N,C,I} <: AbstractArray{T,N}
```

[`RotatingTimeValue`](@ref)のための配列型で、効率のためにフィールド値`rotation`と`time`を2つの配列に格納します。すべての要素のフィールド値を保持する2つの配列は、プロパティとしてアクセスできます。
