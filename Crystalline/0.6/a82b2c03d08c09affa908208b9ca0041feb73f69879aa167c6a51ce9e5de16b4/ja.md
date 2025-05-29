```
Crystalline.RVec{D}(str::AbstractString) --> Crystalline.RVec{D}
Crystalline.RVec(str::AbstractString)    --> Crystalline.RVec
Crystalline.RVec(::AbstractVector, ::AbstractMatrix) --> Crystalline.RVec
Crystalline.RVec{D}(::AbstractVector, ::AbstractMatrix) --> Crystalline.RVec{D}
```

文字列表現 `str` を解析して `Crystalline.RVec` を返します。これは以下のいずれかの形式で供給されます：

```jl
"($1,$2,$3)"
"[$1,$2,$3]"
"$1,$2,$3"
```

ここで、座標 `$1`,`$2`, および `$3` は、分数、小数、および「自由」パラメータ {`'α'`,`'β'`,`'γ'`}（または、同等に {`'u'`,`'v'`,`'w'`} または {`'x'`,`'y'`,`'z'`}）を含む文字列です。

`1/2` のような分数や小数は解析できますが、`/` 以外の特別な演算子を使用すると未定義の動作が発生します（例：`*` を使用しないでください）。

## 例

```jldoctest
julia> Crystalline.RVec("0.25,α,0")
[1/4, α, 0]
```
