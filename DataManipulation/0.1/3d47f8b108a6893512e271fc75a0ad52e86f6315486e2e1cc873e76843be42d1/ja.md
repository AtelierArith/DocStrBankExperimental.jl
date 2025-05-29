```
nest(::NamedTuple, [sr"regex" [=> (ss"sub", ...)], ...])
nest(::StructArray, [sr"regex" [=> (ss"sub", ...)], ...])
```

同じ種類のネストされたオブジェクト（例えば、ネストされた `NamedTuple`）にプロパティのサブセットを入れます。

ネストするプロパティは、正規表現によってコンパイル時に選択されます。結果として得られる名前は、正規表現のグループから抽出されるか、置換文字列によって明示的に指定されます。

# 例

```julia
julia> nest((a_x=1, a_y="2", a_z_z=3, b=:z), sr"(a)_(\w+)" ))
(a=(x=1, y="2", z_z=3), b=:z)

julia> nest( (a_x=1, a_y="2", a_z_z=3, b=:z), sr"(a)_(\w+)" => (ss"x\1", ss"val", ss"\2") ))
(xa=(val=(x=1, y="2", z_z=3),), b=:z)
```
