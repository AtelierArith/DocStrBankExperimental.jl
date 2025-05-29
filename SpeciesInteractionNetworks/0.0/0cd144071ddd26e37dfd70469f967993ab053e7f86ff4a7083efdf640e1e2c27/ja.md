```
structuralmodel(::Type{NicheModel}, species::Integer=10, connectance::AbstractFloat=0.2)
```

与えられた種の数と*期待される*接続性を持つニッチモデルの下で食物網を生成します。ニッチモデルアルゴリズムの性質上、種の豊富さのみが保証されており、接続性が正しいことは保証されていません。

ニッチモデルに関する詳細は[`NicheModel`](@ref)を参照してください。
