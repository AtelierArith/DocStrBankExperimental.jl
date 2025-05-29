```
recurrencestructures(x::AbstractRecurrenceMatrix;
                         diagonal=true,
                         vertical=true,
                         recurrencetimes=true,
                         kwargs...)
```

再帰行列 `x` に含まれる再帰構造のヒストグラムを持つ辞書を返します。キーは、与えられたキーワード引数が `true` の場合に `"diagonal"`、`"vertical"` または `"recurrencetimes"` になります。

## 説明

辞書の各項目は整数のベクターであり、ベクターの `i` 番目の要素は `x` に含まれる長さ `i` のラインの数です。

  * `"diagonal"` は対角線、すなわち再帰的な軌道をカウントします。
  * `"vertical"` は垂直線、すなわち層状の状態をカウントします。
  * `"recurrencetimes"` は再帰的な状態間の垂直距離、すなわち再帰時間をカウントします。

デフォルトでは、行列のすべての点がカウントされます。キーワード引数 `theiler` を渡すことで、主対角線の周りのラインを除外することができます。詳細については、関数 [`rqa`](@ref) の引数を参照してください。

「空の」ヒストグラムは常に `[0]` として表されます。

*注意*: 「再帰時間」のユニークな操作的定義は存在しません。再帰プロットの分析では、通常、Gao と Cai によって定義された「第二種」の再帰時間が考慮されます[1]。すなわち、行列の垂直方向における連続した（しかし分離された）再帰構造間の距離です。しかし、その距離は、垂直の再帰構造が1点より長い場合には一意に定義されません。ここで計算される再帰時間は、連続したラインの中点間の距離であり、ポアンカレ再帰時間[2]のバランスの取れた推定量です。

## 参考文献

[1] J. Gao & H. Cai. "On the structures and quantification of recurrence plots". [*Physics Letters A*, 270(1-2), 75–87 (2000)](https://www.sciencedirect.com/science/article/pii/S0375960100003042?via%3Dihub).

[2] N. Marwan & C.L. Webber, "Mathematical and computational foundations of recurrence quantifications", in: Webber, C.L. & N. Marwan (eds.), *Recurrence Quantification Analysis. Theory and Best Practices*, Springer, pp. 3-43 (2015). ```
