```
Some{T}
```

`Union{Some{T}, Nothing}`内で値の存在の有無を区別するために使用されるラッパー型で、値が存在しない場合（[`nothing`](@ref)）と`nothing`値が存在する場合（すなわち`Some(nothing)`）を区別します。

`Some`オブジェクトによってラップされた値にアクセスするには、[`something`](@ref)を使用してください。
