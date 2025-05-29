'special_pieces(<uc>)'

特別な部分は、冪根群 `𝐆` の単純多様体の分割を形成し、最初に [Spaltenstein1982 chap. III](biblio.htm#spalt82) で定義されました。これは、`d` が「双対写像」であるときの `d^2` のファイバーとして定義されます。別の定義は、特別なクラスのザリスキー閉包のクラスの集合であり、より小さな特別なクラスのザリスキー閉包には含まれないものです。特別なクラスは、スプリンガー対応によって特別なキャラクターの像の支持です。

各部分は、単純共役類の和であるため、Chevie ではクラス番号のリストとして表されます。したがって、特別な部分のリストはクラス番号のリストのリストとして返されます。このリストは、部分の次元が増加する順にソートされ、各部分はクラスの次元が減少する順にソートされるため、特別なクラスが最初にリストされます。

```julia-repl
julia> W=coxgroup(:G,2)
G₂

julia> special_pieces(UnipotentClasses(W))
3-element Vector{Vector{Int64}}:
 [1]
 [4, 3, 2]
 [5]

julia> special_pieces(UnipotentClasses(W,3))
3-element Vector{Vector{Int64}}:
 [1]
 [4, 3, 2, 6]
 [5]
```

上記の例は、特別な部分が特性 3 で異なることを示しています。
