```
readK(infile[, vmax, qmax]; use_err=true)
```

`infile`から部分的なレート行列を読み込みます。オプションで、`vmax`および`qmax`引数を介して基準の最大値を手動で定義できます。そうでなければ、csvファイルのヘッダーから読み取ろうとします。

`use_err` : 不確実性を読み込むかどうか。
