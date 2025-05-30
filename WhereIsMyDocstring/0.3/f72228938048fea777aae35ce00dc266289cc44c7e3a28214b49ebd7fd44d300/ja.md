```
@docmatch f
@docmatch f(sig)
@docmatch f module
@docmatch f(sig) module
```

ブロックに含まれるすべてのドキュメント文字列を取得します

````
```@docs
f
```
````

または

````
```@docs
f(sig)
```
````

オプションの引数 `module` は、`f` を探すモジュールを制御します。

#### 例

```
julia> @docmatch sin
2-element Vector{WhereIsMyDocstring.DocStr}:
 Base.sin
  内容:
    sin(x) [...]
  シグネチャタイプ:
    Tuple{Number}
  ```@docs``` ブロックに含める:
    Base.sin(::Number)
  ソース:
   math.jl:490
================================================================================
 Base.sin
  内容:
    sin(A::AbstractMatrix) [...]
  シグネチャタイプ:
    Tuple{AbstractMatrix{<:Real}}
  ```@docs``` ブロックに含める:
    Base.sin(::AbstractMatrix{<:Real})
  ソース:
    /usr/share/julia/stdlib/v1.10/LinearAlgebra/src/dense.jl:956
```
