```
malloc(T::Type, dims::Int...) -> PtrArray{T, N} <: AbstractArray{T, N}
```

Cのstdlibの`malloc`を使用して、型`T`と次元`dims`の新しい配列を割り当てます。

`T`は`isbitstype`でなければなりません。

この配列はJuliaのガベージコレクタによって追跡されないため、もはや必要なくなったときに[`free`](@ref)を呼び出すのはユーザーの責任です。
