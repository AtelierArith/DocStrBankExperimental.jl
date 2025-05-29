```
isnormal(opsᴳ::AbstractVector{<:SymOperation},
         opsᴴ::AbstractVector{<:SymOperation};
         verbose::Bool=false)                    --> Bool
```

群 $H$ の操作が群 $G$ の中で正規であるかどうかを判断します（それぞれ操作 `opsᴳ` と `opsᴴ` を持つ）、つまり

$$
ghg⁻¹ ∈ H, ∀ g∈G, ∀ h∈H
$$

ブール値の答えを返します（正規であれば `true`、そうでなければ `false`）。

## 注意

これは空間群を比較するものであり、空間群のタイプを比較するものではありません。つまり、この比較は $H$ と $G$ の間で一致する設定の選択を前提としています。異なる従来の設定を持つ空間群のタイプを比較するには、まず共有設定に変換する必要があります。
