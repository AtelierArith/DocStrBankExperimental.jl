```
psi = randMPS(Qlabel,Ns[,m=2,type=Float64,flux=...])
```

は、与えられたサイトに保存されたベクトル `Qlabel` の `qnum` から `Ns` サイトのランダムな MPS を生成します。結合次元 `m`、要素タイプのための `type`、および全体の `flux`（デフォルトは `Qlabel` に指定されたタイプのゼロ）を指定します。
