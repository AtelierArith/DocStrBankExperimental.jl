```
eleid = addelement!(model,ElType,nodid;kwargs...)
```

`model`に1つまたは複数の要素を追加し、`nodid`で指定されたノードに接続します。

`nodid`が`AbstractVector`の場合：モデルに単一の要素を追加します。`eleid`は単一の要素識別子になります。

`nodid`が`AbstractMatrix`の場合：モデルに複数の要素を追加します。`nodid`の各行は単一の要素のノードを識別します。`eleid`は要素識別子のベクトルになります。

各要素について、`addelement!`は`eleobj = ElType(nodes;kwargs...)`を呼び出します。ここで、`nodes`は要素のノードのベクトルです。

参照：[`addnode!`](@ref), [`describe`](@ref), [`coord`](@ref)
