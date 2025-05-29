```
optblocklength(data, bi::BootInput)::Float64
optblocklength(data ; kwargs...)::Float64
```

依存ブートストラップで使用する最適なブロック長の推定値を提供します。

多変量データセットの場合、最適なブロック長はデータの各列について推定され、その後、Vector{Float64}をFloat64にマッピングする関数であるbi.fblocklengthcombineが呼び出され、複数の推定値を単一の推定値に減少させます。fblocklengthcombineのデフォルト値は中央値です。

現在実装されているブロック長メソッドには以下が含まれます：

```
 - Patton, Politis, White (2009) "Correction to Automatic Block Length Selection For the Dependent Bootstrap"
```

上記のすべてのメソッドについて、バンド幅はPolitis (2003) "Adaptive Bandwidth Choice"に従って推定され、その論文で提案されたフラットトップカーネルを使用します。
