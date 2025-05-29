```
index(dgt::AbstractVector{T}; base::Integer=2, dtype::DataType=T) where T <: Integer
```

桁を整数インデックスに変換するには、次の関係を使用します：

```
number = ∑ᵢ bits[i] * base^(L-i) + 1
```

総和は効率的な多項式評価法を使用して評価されます。

## 入力:

  * `dgt`  : 桁。
  * `base` : 基数。
