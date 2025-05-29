```
PtrArray(ptr::Ptr{T}, dims::Int...; check_dims=true) <: DenseArray{T}
```

ポインタを標準のJuliaメモリ順序に従った`DenseArray`インターフェースに準拠する`PtrArray`でラップします。

`check_dims`がtrueの場合、`dims`が非負であり、掛け算したときにオーバーフローしないことを検証します。`check_dims=false`に設定し、負の値やオーバーフローした`dims`を使用すると、奇妙なことが起こる可能性があります。

!!! note
    Juliaのガベージコレクタは`Ptr`を追跡できないため、ユーザーは`ptr + prod(dims) - 1`を通じて`ptr`が指すメモリが`PtrArray`が使用されている間ずっと確保されていることを保証し、`PtrArray`に格納された可変オブジェクトがガベージコレクションされないようにする責任があります。


関連情報は[`malloc`](@ref)、[`free`](@ref)を参照してください。
