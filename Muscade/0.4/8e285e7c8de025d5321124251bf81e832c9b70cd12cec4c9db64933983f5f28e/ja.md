```
eleres = getresult(state,req,els)
```

ネストされた `NamedTuples` と `NTuples` の配列を取得し、要素の結果を得ます。`req` は `@request` を使用して定義されたリクエストです。`state` は `State` のベクターまたは単一の `State` です。`els` は次のいずれかです。

  * 同じ具体的な要素タイプに対応する `EleID` のベクター（`addelement!` から取得）
  * 具体的な要素タイプ（[`eletyp`](@ref) を参照）。

`state` がベクターの場合、出力 `dofres` のサイズは `(nele,nstate)` です。`state` がスカラーの場合、出力 `dofres` のサイズは `(nele)` です。

参照: [`getdof`](@ref), [`@request`](@ref), [`@espy`](@ref), [`addelement!`](@ref), [`solve`](@ref), [`eletyp`](@ref)
