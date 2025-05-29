ストアバウンド制約 $[l,u]$

`NaN` コンポーネントの存在と $l\le u$ 条件は構築時にチェックされます。ただし、一部のコンポーネントは無限である可能性があります。

# コンストラクタ

以下のコンストラクタが利用可能です：

  * $$
    [0.0,1.0]^n
    $$

    を構築します

```julia
BoundConstraints(n)
```

  * コンポーネントが型 `T` の $[T(0),T(1)]^n$ を構築します

```julia
BoundConstraints(T,n)
```

  * `l` と `u` が下限および上限ベクトルである $[l,u]$ を構築します

```julia
BoundConstraints(l,u)
```

# 関連関数

  * [`Base.eltype(bc::BoundConstraints{ELT}) where ELT`](@ref)
  * [`Base.axes(bc::BoundConstraints)`](@ref)
  * [`Base.length(bc::BoundConstraints)`](@ref)
  * [`Base.size(bc::BoundConstraints)`](@ref)
  * [`in(x::AbstractArray{<:Real,N},bc::BoundConstraints{<:Real,N}) where N`](@ref)
  * [`lower_bound(bc::BoundConstraints)`](@ref)
  * [`upper_bound(bc::BoundConstraints)`](@ref)
  * [`project!(x::AbstractArray{<:Real,N},bc::BoundConstraints{<:Real,N}) where N`](@ref)
  * [`Base.:-(bc::BoundConstraints,τ::AbstractArray)`](@ref)
  * [`Base.:+(bc::BoundConstraints,τ::AbstractArray)`](@ref)
