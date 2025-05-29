```
dms_single_site(arnet::ArNet, arvar::ArVar, seqid::Int; pc::Float64=0.1)
```

参照配列 `seqid` のすべての単一サイト変異体に対して `-log(P(mut))/log(P(seq))` を含む `q×L` 行列を返し、スコアが意味を持たず、慣例的に `+Inf` に設定されるギャップを含む参照配列の残基のインデックスのベクトルを返します。負の値は有益な変異を示し、値 0 は野生型アミノ酸を示します。
