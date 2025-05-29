```
state(s::Index, name::String; kwargs...)
```

インデックス `s` に対して `name` という名前の状態に対応する ITensor を返します。返される ITensor は `s` を唯一のインデックスとして持ちます。

ここでの用語は、物理学における単一サイト状態または波動関数のアイデアに基づいています。

`state` 関数は、インデックス `s` のタグのいずれかに対応する `SiteType` 引数と、入力状態名に対応する `StateName"name"` 引数を取る `state` または `state!` メソッドをオーバーロードすることによって、さまざまなインデックスタグに対して実装されています。

`state` システムは、MPS タイプによって積状態 MPS を構築するためやその他の目的で使用されます。

# 例

```julia
s = Index(2, "Site,S=1/2")
sup = state(s,"Up")
sdn = state(s,"Dn")
sxp = state(s,"X+")
sxm = state(s,"X-")
```
