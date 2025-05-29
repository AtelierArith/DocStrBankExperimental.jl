```
findall_nan_chunks!(v, x)
```

`x`内の各`NaN`チャンクの（開始、停止）インデックスを見つけ、`NaN`の位置を追跡するために、`length(x) == length(v)`である事前に割り当てられたブールベクトル`v`を使用して、それらのインデックスタプルのベクトルを返します。

参照: [`findall_nan_chunks`](@ref)

## 例

```julia
x = [NaN, NaN, 2.3, NaN, 5.6, NaN, NaN, NaN]
v = zeros(Bool, length(x))
findall_nan_chunks!(v, x)
```
