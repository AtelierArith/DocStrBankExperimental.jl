**単変数**

```
evaluate(n::Int,x::Array{<:Real},a::AbstractVector{<:Real},b::AbstractVector{<:Real})
evaluate(n::Int,x::Real,a::AbstractVector{<:Real},b::AbstractVector{<:Real})
evaluate(n::Int,x::AbstractVector{<:Real},op::AbstractOrthoPoly)
evaluate(n::Int,x::Real,op::AbstractOrthoPoly)
```

点 `x` で `n` 番目の単変数基底多項式を評価します。この関数は、合成型 `AbstractOrthoPoly` との使用を容易にするために複数ディスパッチされています。

複数の基底多項式（`ns` に格納されている）を点 `x` で評価する場合は、次のように呼び出します。

```
evaluate(ns::AbstractVector{<:Int},x::AbstractVector{<:Real},op::AbstractOrthoPoly) = evaluate(ns,x,op.α,op.β)
evaluate(ns::AbstractVector{<:Int},x::Real,op::AbstractOrthoPoly) = evaluate(ns,[x],op)
```

*すべて*の基底多項式を点 `x` で評価する場合は、次のように呼び出します。

```
evaluate(x::AbstractVector{<:Real},op::AbstractOrthoPoly) = evaluate(collect(0:op.deg),x,op)
evaluate(x::Real,op::AbstractOrthoPoly) = evaluate([x],op)
```

これにより、次元が `(length(x),op.deg+1)` の配列が返されます。

!!! note
      * `n` は単変数基底多項式の次数です
      * `length(x) = N` で、ここで `N` は点の数です
      * `(a,b)` は再帰係数です


**多変数**

```
evaluate(n::AbstractVector{<:Int},x::AbstractMatrix{<:Real},a::Vector{<:AbstractVector{<:Real}},b::Vector{<:AbstractVector{<:Real}})
evaluate(n::AbstractVector{<:Int},x::AbstractVector{<:Real},a::Vector{<:AbstractVector{<:Real}},b::Vector{<:AbstractVector{<:Real}})
evaluate(n::AbstractVector{<:Int},x::AbstractMatrix{<:Real},op::MultiOrthoPoly)
evaluate(n::AbstractVector{<:Int},x::AbstractVector{<:Real},op::MultiOrthoPoly)
```

点 `x` で n 番目の p-変数基底多項式を評価します。この関数は、合成型 `MultiOrthoPoly` との使用を容易にするために複数ディスパッチされています。

複数の基底多項式を点 `x` で評価する場合は、次のように呼び出します。

```
evaluate(ind::AbstractMatrix{<:Int},x::AbstractMatrix{<:Real},a::Vector{<:AbstractVector{<:Real}},b::Vector{<:AbstractVector{<:Real}})
evaluate(ind::AbstractMatrix{<:Int},x::AbstractMatrix{<:Real},op::MultiOrthoPoly)
```

ここで `ind` は多重インデックスの行列です。

*すべて*の基底多項式を点 `x` で評価する場合は、次のように呼び出します。

```
evaluate(x::AbstractMatrix{<:Real},mop::MultiOrthoPoly) = evaluate(mop.ind,x,mop)
```

これにより、次元が `(mop.dim,size(x,1))` の配列が返されます。

!!! note
      * `n` は多重インデックスです
      * `length(n) == p` で、すなわち p-変数基底多項式です
      * `size(x) = (N,p)` で、ここで `N` は点の数です
      * `size(a)==size(b)=p` です。

