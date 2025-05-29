```
describe(model,spec)
```

`model`に関する情報を出力します。`spec`は以下のいずれかです。

  * 要素を説明するための`EleID`
  * 自由度を説明するための`DofID`
  * ノードを説明するための`NodID`
  * 自由度タイプのリストを取得するための`:doftyp`
  * 自由度のリストを取得するための`:dof`
  * 要素タイプのリストを取得するための`:eletyp`

参照: [`addelement!`](@ref), [`addnode!`](@ref)
