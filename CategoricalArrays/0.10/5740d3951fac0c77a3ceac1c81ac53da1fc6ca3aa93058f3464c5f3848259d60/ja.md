```
cut(x::AbstractArray, breaks::AbstractVector;
    labels::Union{AbstractVector,Function},
    extend::Union{Bool,Missing}=false, allowempty::Bool=false)
```

数値配列を `breaks` の値で区間に分割し、各エントリがどの区間に属するかを示す順序付きの `CategoricalArray` を返します。区間は `[lower, upper)` の形式であり、すなわち下限は含まれ、上限は除外されます。ただし、`extend=true` の場合は、最後の区間は両端が閉じられた形になります。すなわち、`[lower, upper]` となります。

`x` が欠損値を受け入れる場合（すなわち `eltype(x) >: Missing`）、返される配列もそれを受け入れます。

# キーワード引数

  * `extend::Union{Bool, Missing}=false`: `false` の場合、`x` のいくつかの値がブレークの外にあるとエラーが発生します。`true` の場合、`x` のすべての値を含むようにブレークが自動的に追加され、上限は最後の区間に含まれます。`missing` の場合、ブレークの外にある値は `missing` エントリを生成します。
  * `labels::Union{AbstractVector, Function}`: 区間に使用する名前を与える文字列、文字、または数値のベクトル；または、左と右の区間の境界およびグループインデックスからラベルを生成する関数 `f(from, to, i; leftclosed, rightclosed)`。デフォルトは `"[from, to)"` （または `extend == true` の場合は最右の区間に対して `"[from, to]"`）。
  * `allowempty::Bool=false`: `false` の場合、いくつかのブレークが複数回現れるとエラーが発生し、空の区間が生成されます。`true` の場合、重複するブレークが許可され、それによって生成される区間は未使用のレベルとして保持されます（ただし、重複するラベルは許可されません）。

# 例

```jldoctest
julia> using CategoricalArrays

julia> cut(-1:0.5:1, [0, 1], extend=true)
5-element CategoricalArray{String,1,UInt32}:
 "[-1.0, 0.0)"
 "[-1.0, 0.0)"
 "[0.0, 1.0]"
 "[0.0, 1.0]"
 "[0.0, 1.0]" 

julia> cut(-1:0.5:1, 2)
5-element CategoricalArray{String,1,UInt32}:
 "Q1: [-1.0, 0.0)"
 "Q1: [-1.0, 0.0)"
 "Q2: [0.0, 1.0]"
 "Q2: [0.0, 1.0]"
 "Q2: [0.0, 1.0]" 

julia> cut(-1:0.5:1, 2, labels=["A", "B"])
5-element CategoricalArray{String,1,UInt32}:
 "A"
 "A"
 "B"
 "B"
 "B" 

julia> cut(-1:0.5:1, 2, labels=[-0.5, +0.5])
5-element CategoricalArray{Float64,1,UInt32}:
 -0.5
 -0.5
 0.5
 0.5
 0.5

julia> fmt(from, to, i; leftclosed, rightclosed) = "grp $i ($from//$to)"
fmt (generic function with 1 method)

julia> cut(-1:0.5:1, 3, labels=fmt)
5-element CategoricalArray{String,1,UInt32}:
 "grp 1 (-1.0//-0.3333333333333335)"
 "grp 1 (-1.0//-0.3333333333333335)"
 "grp 2 (-0.3333333333333335//0.33333333333333326)"
 "grp 3 (0.33333333333333326//1.0)"
 "grp 3 (0.33333333333333326//1.0)"
```
