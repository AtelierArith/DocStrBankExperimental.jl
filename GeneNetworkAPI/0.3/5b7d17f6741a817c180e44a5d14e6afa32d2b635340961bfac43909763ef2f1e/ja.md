```markdown
make*rectangular(v*arrays::Vector{Vector{T}} where T)

任意の型の配列の配列を受け取り、`String`の行列に変換します。配列は異なる型と長さを持つことができます。データを長方形にするために、デフォルトでは`filler`引数を使用し、`filler`は空の文字列です。

## 例 1

```

julia julia> myArrayOfArrays = [["A1","A2", "A3"], ["B1", "B2"], ["C1","C2"]]; julia> make_rectangular(test) 3×3 Matrix{String}: "A1"  "B1"  "C1" "A2"  "B2"  "C2" "A3"  ""    ""

```

## 例 2

```

julia julia> myArrayOfArrays = [["A1","A2", "A3"], [1, 2], ["C1","C2"]]; julia> make_rectangular(test) 3×3 Matrix{String}: "A1"  "1"  "C1" "A2"  "2"  "C2" "A3"  ""    ""

```

```
