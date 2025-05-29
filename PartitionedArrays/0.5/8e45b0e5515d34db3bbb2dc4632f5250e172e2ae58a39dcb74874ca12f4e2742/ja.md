```
struct JaggedArray{T,Ti}
```

ベクトルのベクトルの効率的な実装。内部ベクトルは、補助ベクトル `data` を使用して、連続したメモリ位置に一つずつ格納されます。各内部ベクトルに対応するインデックスの範囲は、整数のベクトル `ptrs` を使用してエンコードされます。

# プロパティ

```
data::Vector{T}
ptrs::Vector{Ti}
```

`a::JaggedArray` が与えられた場合、`a.data` には内部ベクトルが含まれています。`i` 番目の内部ベクトルは、範囲 `a.ptrs[i]:(a.ptrs[i+1]-1)` に格納されています。内部ベクトルの数（すなわち `length(a)`）は `length(a.ptrs)-1` です。`a[i]` は、範囲 `a.ptrs[i]:(a.ptrs[i+1]-1)` に制限された `a.data` のビューを返します。

# スーパタイプ階層

```
JaggedArray{T,Ti} <: AbstractVector{V}
```

`a::JaggedArray` が与えられた場合、`V` は `typeof(view(a.data,a.ptrs[i]:(a.ptrs[i+1]-1)))` です。
