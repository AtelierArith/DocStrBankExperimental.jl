```
Pl(x, l::Integer; [norm = Val(:standard)])
```

引数 `x` と次数 `l` に対してレジェンドル多項式 $P_\ell(x)$ を計算します。

デフォルトのノルムは `Val(:standard)` に設定されており、この場合、多項式はすべての `l` に対して `Pl(1, l) == 1` を満たします。オプションで、ノルムを `Val(:normalized)` に設定することで、正規化されたレジェンドル多項式を取得できます。これらは L2 ノルムが `1` です。

# 例

```jldoctest
julia> Pl(1, 2)
1.0

julia> Pl(0.5, 4) ≈ -37/128 # 分析的に得られた値
true

julia> Pl(0.5, 20, norm = Val(:normalized))
-0.21895188261094017
```
