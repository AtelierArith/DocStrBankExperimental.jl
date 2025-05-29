```
expand(x::SurrealFinite; level=0)
```

サーリアルを異なるレベルの展開で文字列として書き出します。

## 引数

  * `x::SurrealFinite`: 展開する要素の数
  * `level=0`: 展開の量

      * 0 : 省略形が存在する場合はそれを書き出し、存在しない場合は $\{ X_L \| X_R \}$ とします
      * 1 : $\{ X_L \| X_R \}$
      * 2 : $X_L$ と $X_R$ を再帰的に展開します

## 例

```jldoctest
julia> expand( convert(SurrealFinite, 2))
"2"
julia> expand( convert(SurrealFinite, 2); level=1)
"{ 1 | ∅ }"
julia> expand( convert(SurrealFinite, 2); level=2)
"{ { { ∅ | ∅ } | ∅ } | ∅ }"
```
