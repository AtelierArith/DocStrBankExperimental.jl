```
lift(k, m)
```

低次元代数 k のメンバー（Multivector、KVector、または Blade）を、非ユークリッド基底 1-blade m を含む別の代数の偶数部分代数に持ち上げます。持ち上げによって生成される二重ベクトルは、元のメンバーと同型です。

例:

```
julia> module f3
         using Multivectors
         @generate_basis("++-")
       end

julia> using .f3

julia> @generate_basis("++") 

julia> lift.([1e₁, 2e₂, 12e₁₂], f3.e₃)
3-element Array{Blade{Int64,2},1}:
  1Main.f3.e₁₃
  2Main.f3.e₂₃
 12Main.f3.e₁₂

julia> ans .* ans
3-element Array{Int64,1}:
    1
    4
 -144

julia> [1e₁, 2e₂, 12e₁₂] .* [1e₁, 2e₂, 12e₁₂]
3-element Array{Int64,1}:
    1
    4
 -144
```
