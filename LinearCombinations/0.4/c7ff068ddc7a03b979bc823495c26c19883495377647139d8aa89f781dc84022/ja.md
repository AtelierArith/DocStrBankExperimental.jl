```
MultilinearExtension(f)
MultilinearExtension(f, name)
```

この型の要素は `f` の多重線形拡張です。表示される名前を追加で指定することもできます。

# 例

```jldoctest
julia> a, b = Linear('x' => 1, 'y' => 2), Linear("z" => 1.0, "w" => -1.0)
(Linear{Char, Int64}('x' => 1, 'y' => 2), Linear{String, Float64}("w" => -1.0, "z" => 1.0))

julia> const concat = MultilinearExtension(*, "concat")
concat

julia> concat(a, b)
Linear{String, Float64} with 4 terms:
-"xw"+2.0*"yz"-2.0*"yw"+"xz"
```
