```
irfft(A, d [, dims])
```

[`rfft`](@ref) の逆: 複素配列 `A` に対して、FFT が `A` を前半に持つ対応する実配列を返します。[`rfft`](@ref) と同様に、`dims` は変換する次元のオプションのサブセットで、デフォルトは `1:ndims(A)` です。

`d` は、`dims[1]` 次元に沿った変換された実配列の長さであり、`div(d,2)+1 == size(A,dims[1])` を満たさなければなりません。（このパラメータは `size(A)` から推測できません。なぜなら、`2*size(A,dims[1])-2` と `2*size(A,dims[1])-1` の両方が変換された実配列の有効なサイズだからです。）
