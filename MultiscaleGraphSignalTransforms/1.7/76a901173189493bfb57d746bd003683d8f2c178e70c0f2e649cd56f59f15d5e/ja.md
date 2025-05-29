```
LPHGLET_dictionary(GP::GraphPart, G::GraphSig; gltype::Symbol = :L, ϵ::Float64 = 0.3)
```

全体のLP-HGLET辞書を組み立てます

### 入力引数

  * `GP`: GraphPartオブジェクト
  * `G`:  GraphSigオブジェクト
  * `gltype`: `:L`または`:Lsym`
  * `ϵ`: 相対アクション帯域幅（デフォルト: 0.3）

### 出力引数

  * `dictionary`: LP-HGLET辞書
