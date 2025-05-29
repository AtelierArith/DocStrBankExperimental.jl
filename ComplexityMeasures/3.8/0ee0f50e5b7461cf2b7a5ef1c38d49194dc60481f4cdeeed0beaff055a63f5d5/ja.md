```
UniqueElementsEncoding <: Encoding
UniqueElementsEncoding(x)
```

`UniqueElementsEncoding` は、各 `xᵢ ∈ unique(x)` を正の整数のいずれかにエンコードする汎用エンコーディングです。`xᵢ` は、入力データにおける最初の出現順に従ってエンコードされます。

コンストラクタは入力データ `x` を必要とします。なぜなら、可能なシンボルの数は `length(unique(x))` だからです。

## 例

```julia
using ComplexityMeasures
x = ['a', 2, 5, 2, 5, 'a']
e = UniqueElementsEncoding(x)
encode.(Ref(e), x) == [1, 2, 3, 2, 3, 1] # true
```
