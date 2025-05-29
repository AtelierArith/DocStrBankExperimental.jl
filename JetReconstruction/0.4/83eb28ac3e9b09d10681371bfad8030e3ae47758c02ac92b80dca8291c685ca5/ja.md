```
loadjets!(filename, jets; splitby=isspace, constructor=(px,py,pz,E)->LorentzVectorHEP(E,px,py,pz), dtype=Float64)
```

ファイルから `jets` を読み込みます。 `'#'` で始まる行は無視されます。各行は次のように処理されます：行は `split(line, splitby)` またはデフォルトで単に `split(line)` を使用して分割されます。この行のすべての値は `dtype`（デフォルトでは `Float64`）に変換されます。これらの値は `constructor` 関数の引数として使用され、個々のジェットを生成する必要があります。デフォルトでは、`constructor` はローレンツベクトルを構築します。

`jets` に既に存在するものは影響を受けず、`push!` のみを使用します。

# 例

```julia
# 2つのファイルから1つの配列にジェットを読み込む
jets = []
loadjets!("myjets1.dat", jets)
loadjets!("myjets2.dat", jets)
```
