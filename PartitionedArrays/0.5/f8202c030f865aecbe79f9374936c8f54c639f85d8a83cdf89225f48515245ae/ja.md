```
struct GenericJaggedArray{V,A,B}
```

`JaggedArray`の一般化であり、フィールド`data`と`ptrs`は任意の配列のようなオブジェクトであることが許可されています。

# プロパティ

```
data::A
ptrs::B
```

# スーパタイプ階層

```
GenericJaggedArray{V,A,B} <: AbstractVector{V}
```

`a::GenericJaggedArray`が与えられた場合、`V`は`typeof(view(a.data,a.ptrs[i]:(a.ptrs[i+1]-1)))`です。
