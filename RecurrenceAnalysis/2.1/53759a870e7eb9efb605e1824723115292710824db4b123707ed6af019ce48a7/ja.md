```
recurrencerate(R[; theiler])
```

再帰行列 `R` の再帰率を計算します。

## 説明

再帰率は次のように計算されます：

$$
RR = \frac{1}{S} \sum R
$$

ここで、$S$ は `R` のサイズまたは再帰点の可能性がある `R` の領域です。その分母の定義は一意ではなく、多くの文献では行列の全サイズとして定義されています（例：[1]）、他の文献ではカウントから除外される LOI の点を取り除くように調整されています [2,3]。

`RecurrenceMatrix` または `JointRecurrenceMatrix` 型の行列では、通常中央対角線の周りの点が除外されるため、分母は Theiler ウィンドウの外側の行列のサイズに調整されます（デフォルトでは LOI と等しく、キーワード引数 `theiler` で調整可能です；詳細は [`rqa`](@ref) を参照してください）。`CrossRecurrenceMatrix` 型の行列では、通常すべての点が分析されるため、分母は常に行列の全サイズであり、定義される可能性のある Theiler ウィンドウに関係なく（デフォルトではなし）なります。

*ヒント*: 分母に行列の全サイズを使用する式に従って計算を再現するには、`RecurrenceMatrix(s,ε)` の代わりに `CrossRecurrenceMatrix(s,s,ε)` を使用して再帰行列を定義し、LOI やその周りの他の対角線を明示的に除外するために `theiler=1`（または一般的には `theiler=n`）を設定します。

## 参考文献

[1] : N. Marwan *et al.*, "Recurrence plots for the analysis of complex systems", *Phys. Reports 438*(5-6), 237-329 (2007). [DOI:10.1016/j.physrep.2006.11.001](https://doi.org/10.1016/j.physrep.2006.11.001)

[2] : C.L. Webber & J.P. Zbilut, "Recurrence Quantification Analysis of Nonlinear Dynamical Systems", in: Riley MA & Van Orden GC, Tutorials in Contemporary Nonlinear Methods for the Behavioral Sciences, 26-94 (2005). URL: https://www.nsf.gov/pubs/2005/nsf05057/nmbs/nmbs.pdf

[3] : N. Marwan & C.L. Webber, "Mathematical and computational foundations of recurrence quantifications", in: Webber, C.L. & N. Marwan (eds.), *Recurrence Quantification Analysis. Theory and Best Practices*, Springer, pp. 3-43 (2015).
