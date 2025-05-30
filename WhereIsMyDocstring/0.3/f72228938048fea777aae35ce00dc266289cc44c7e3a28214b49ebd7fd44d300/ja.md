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
  Content:
    sin(x) [...]
  Signature type:
    Tuple{Number}
  Include in ```@docs``` block:
    Base.sin(::Number)
  Source:
   math.jl:490
================================================================================
 Base.sin
  Content:
    sin(A::AbstractMatrix) [...]
  Signature type:
    Tuple{AbstractMatrix{<:Real}}
  Include in ```@docs``` block:
    Base.sin(::AbstractMatrix{<:Real})
  Source:
    /usr/share/julia/stdlib/v1.10/LinearAlgebra/src/dense.jl:956
```
