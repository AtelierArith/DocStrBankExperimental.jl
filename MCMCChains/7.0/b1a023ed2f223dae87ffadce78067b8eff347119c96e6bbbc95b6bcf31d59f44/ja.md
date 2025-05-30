```
group(chains::Chains, name::Union{AbstractString,Symbol}; index_type::Symbol=:bracket)
```

同じ `name` を持つパラメータの異なるインデックスを含むチェーンのサブセットを返します。

デフォルトでは、`name[index]` の形式のブラケットインデックスが想定されています。ドットインデックスを持つパラメータには `index_type=:dot` を使用します。すなわち、`:sym.index` の形式です。
