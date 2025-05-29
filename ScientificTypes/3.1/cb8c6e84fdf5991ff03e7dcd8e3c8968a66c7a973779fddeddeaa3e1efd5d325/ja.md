```
coerce(A, S)
```

新しい配列 `A` を返します。その科学的要素型は `S` です。

```
julia> v = coerce([3, 7, 5], Continuous)
3-element Vector{Float64}:
 3.0
 7.0
 5.0

julia> scitype(v)
AbstractVector{Continuous}

```

```
coerce(X, specs...; tight=false, verbosity=1)
```

テーブル `X` を与えられた場合、`X` のコピーを返し、列の要素の scitypes が新しい仕様 `specs` に一致することを保証します。有効な仕様は3つあります：

(i) 1つ以上の `column_name=>Scitype` ペア：

```
coerce(X, col1=>Scitype1, col2=>Scitype2, ... ; verbosity=1)
```

(ii) 1つ以上の `OldScitype=>NewScitype` ペア（`OldScitype` は `OldScitype` と `Union{Missing,OldScitype}` の両方のケースをカバーします）：

```
coerce(X, OldScitype1=>NewScitype1, OldScitype2=>NewScitype2, ... ; verbosity=1)
```

(iii) 列名をキーとした科学的型の辞書：

```
coerce(X, d::AbstractDict{<:ColKey, <:Type}; verbosity=1)
```

ここで `ColKey = Union{Symbol,AbstractString}` です。

### 例

`column_name=>Scitype` ペアを指定：

```
using CategoricalArrays, DataFrames, Tables
X = DataFrame(name=["Siri", "Robo", "Alexa", "Cortana"],
              height=[152, missing, 148, 163],
              rating=[1, 5, 2, 1])
Xc = coerce(X, :name=>Multiclass, :height=>Continuous, :rating=>OrderedFactor)
schema(Xc).scitypes # (Multiclass, Continuous, OrderedFactor)
```

`OldScitype=>NewScitype` ペアを指定：

```
X  = (x = [1, 2, 3],
      y = rand(3),
      z = [10, 20, 30])
Xc = coerce(X, Count=>Continuous)
schema(Xfixed).scitypes # (Continuous, Continuous, Continuous)
```
