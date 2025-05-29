```
arecompatible(x::OutputVar, y::OutputVar)
```

二つの `OutputVar` が同じ物理空間で定義されているかどうかを返します。

これは `dims` と `dim_attributes` を比較することで実現されます（後者は単位に関する情報を含む可能性があるためです）。

私たちは以下を仮定します：

  * `dim2index` と `index2dim` が正しく作成されており、`dims` を反映している
  * `data` も `dims` と一貫している

私たちはまた、`data` の単位を*確認しません*。
