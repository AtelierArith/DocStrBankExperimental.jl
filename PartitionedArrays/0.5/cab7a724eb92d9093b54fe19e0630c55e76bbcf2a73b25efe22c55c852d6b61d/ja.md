```
length_to_ptrs!(ptrs)
```

[`JaggedArray`](@ref)のフィールド`ptrs`を計算します。`length(ptrs)`は、ジャグged配列のサブベクトルの数に1を加えたものになるべきです。入力時、`ptrs[i+1]`はi番目のサブベクトルの長さです。出力時、`ptrs[i]:(ptrs[i+1]-1)`は、i番目のサブベクトルがジャグged配列の`data`フィールドに格納されている範囲を含みます。
