```
recode(a::AbstractArray[, default::Any], pairs::Pair...)
```

`a`のコピーを返し、`pairs`のキーに一致する要素を対応する値で置き換えます。配列の型は、すべての再コーディングされた要素を保持できるように選択されます（ただし、必ずしも`a`の元の要素を保持するわけではありません）。

`pairs`の各`Pair`について、要素がキー（ペアの最初の項目）と等しい場合（`isequal`に従って）または`in`の場合、対応する値（2番目の項目）が使用されます。要素がキーに一致せず、`default`が提供されていないか`nothing`の場合、そのままコピーされます。`default`が指定されている場合は、元の要素の代わりに使用されます。要素が複数のキーに一致する場合、最初の一致が使用されます。

```
recode(a::CategoricalArray[, default::Any], pairs::Pair...)
```

`a`が`CategoricalArray`の場合、結果のレベルの順序は渡された`pairs`の順序によって決定され、`default`が提供されている場合は最後のレベルになります。

# 例

```jldoctest
julia> using CategoricalArrays

julia> recode(1:10, 1=>100, 2:4=>0, [5; 9:10]=>-1)
10-element Vector{Int64}:
 100
   0
   0
   0
  -1
   6
   7
   8
  -1
  -1

```

```
 recode(a::AbstractArray{>:Missing}[, default::Any], pairs::Pair...)
```

`a`に欠損値が含まれている場合、それらは決して`default`で置き換えられません：ペアで`missing`を使用して再コーディングしてください。そうでない場合、返される配列は欠損値を受け入れます。

# 例

```jldoctest
julia> using CategoricalArrays

julia> recode(1:10, 1=>100, 2:4=>0, [5; 9:10]=>-1, 6=>missing)
10-element Vector{Union{Missing, Int64}}:
 100
   0
   0
   0
  -1
    missing
   7
   8
  -1
  -1    

```
