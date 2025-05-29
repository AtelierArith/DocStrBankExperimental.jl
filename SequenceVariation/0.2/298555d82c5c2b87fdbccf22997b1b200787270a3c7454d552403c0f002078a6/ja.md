```
Variation{S<:BioSequence,T<:BioSymbol}
```

生物学的配列への単一の変更。配列特有の [`Substitution`](@ref)、[`Deletion`](@ref) または [`Insertion`](@ref) を表すことができる一般的なラッパーです。`Variation` は参照配列の含有と組み込みの検証により、[`Edit`](@ref) よりも堅牢です。

# コンストラクタ

```
Variation(ref::S, e::Edit{S,T}) where {S<:BioSequence,T<:BioSymbol}
Variation(ref::S, edit::AbstractString) where {S<:BioSequence}
```

一般的に、`Edit` コンストラクタは正確性を確保するために避けるべきです：[`variations(::Haplotype)`](@ref) の使用が推奨されます。

`AbstractString` から `Variation` を構築することは、次の構文を使用して `edit` から解析されます：

  * 置換: `"<REFBASE><POS><ALTBASE>"`、例: `"G16C"`
  * 削除: `"Δ<STARTPOS>-<ENDPOS>"`、例: `"Δ1-2"`
  * 挿入: `"<POS><ALTBASES>"`、例: `"11T"`
