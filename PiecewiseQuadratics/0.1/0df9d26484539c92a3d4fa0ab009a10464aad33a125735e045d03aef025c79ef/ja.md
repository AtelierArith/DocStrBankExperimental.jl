```
intersect(f_list::Vector{BoundedQuadratic})
```

可能であれば、BoundedQuadraticのリストのドメインを交差させます。

# 例

```julia
julia> f_list = [BoundedQuadratic(-100, 100, 1, 1, 1),
          BoundedQuadratic(-50, 25, 1, 1, 1),
          BoundedQuadratic(0, 50, 1, 1, 1)]
3-element Vector{BoundedQuadratic}:
 BoundedQuadratic: f(x) = 1.00000 x² + 1.00000 x + 1.00000, ∀x ∈ [-100.00000, 100.00000]

 BoundedQuadratic: f(x) = 1.00000 x² + 1.00000 x + 1.00000, ∀x ∈ [-50.00000, 25.00000]

 BoundedQuadratic: f(x) = 1.00000 x² + 1.00000 x + 1.00000, ∀x ∈ [0.00000, 50.00000]

julia> out, valid = intersect(f_list);

julia> valid
true

julia> out
3-element Vector{BoundedQuadratic}:
 BoundedQuadratic: f(x) = 1.00000 x² + 1.00000 x + 1.00000, ∀x ∈ [0.00000, 25.00000]

 BoundedQuadratic: f(x) = 1.00000 x² + 1.00000 x + 1.00000, ∀x ∈ [0.00000, 25.00000]

 BoundedQuadratic: f(x) = 1.00000 x² + 1.00000 x + 1.00000, ∀x ∈ [0.00000, 25.00000]


julia> f_list = [BoundedQuadratic(-100, 0, 1,1,1)
            BoundedQuadratic(25, 50, 1,1,1)]  # 非重複
2-element Vector{BoundedQuadratic}:
 BoundedQuadratic: f(x) = 1.00000 x² + 1.00000 x + 1.00000, ∀x ∈ [-100.00000, 0.00000]

 BoundedQuadratic: f(x) = 1.00000 x² + 1.00000 x + 1.00000, ∀x ∈ [25.00000, 50.00000]

julia> out, valid = intersect(f_list);

julia> valid
false

julia> out
2-element Vector{BoundedQuadratic}:
 #undef
 #undef

```
