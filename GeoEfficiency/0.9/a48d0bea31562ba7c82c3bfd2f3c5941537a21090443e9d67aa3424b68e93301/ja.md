```
source(anchorPnt::Point = Point())
```

入力に従ってソース（`anchorPnt`、`SrcRadius`、`SrcLength`）を説明するタプルを返します。

  * `anchorPnt` : ソースのアンカーポイント。これが欠けている場合、ユーザーは`console`を通じて入力を促されます。
  * `SrcRadius` : ソース半径。
  * `SrcLength` : ソースの長さ。

!!! warning
    ソースタイプがポイントソースに設定されている場合、`SrcRadius`と`SrcLength`は両方ともゼロに設定されます。詳細については、**参照してください:** [`typeofSrc()`](@ref) および [`typeofSrc(x::Int)`](@ref)。

