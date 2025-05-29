```
set_precision!(f, ::Type{Balls}, n::Int)
```

`f`の期間中、ボールの算術精度を`n`に変更します。

# 例

```jldoctest
julia> set_precision!(Balls, 4) do
         const_pi(RealField())
       end
[3e+0 +/- 0.376]

julia> set_precision!(Balls, 200) do
         const_pi(RealField())
       end
[3.1415926535897932385 +/- 3.74e-20]
```
