```
BlockData{T, TV<:AbstractVector{T}, TX<:AbstractVector{TV}} <: AbstractVector{T}
```

`AbstractVector`の厳密に順序付けられたコレクションで、データのラグド配列を表します。

`GPPP`を扱う際に非常に便利です。例えば

```julia
f = @gppp let
    f1 = GP(SEKernel())
    f2 = GP(Matern52Kernel())
    f3 = f1 + f2
end

# `f`の`f2`および`f3`プロセスにインデックスを付けるために使用できる`BlockData`セットを指定します。
x = BlockData(
    GPPPInput(:f2, randn(4)),
    GPPPInput(:f3, randn(3)),
)

# 入力で`f`にインデックスを付けます。
f(x)
```
