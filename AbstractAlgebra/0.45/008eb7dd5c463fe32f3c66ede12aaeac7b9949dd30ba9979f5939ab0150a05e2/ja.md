```
map_from_func(image_fn::Function, domain, codomain)
```

親オブジェクト $R$ と $S$ によって与えられるドメインとコドメインを持つ一般的な関数マップを構築します。これはJulia関数 $f$ に対応します。

# 例

```jldoctest
julia> f = map_from_func(x -> x + 1, ZZ, ZZ)
Julia関数によって定義されたマップ
  整数から
  整数へ

julia> f(ZZ(2))
3
```
