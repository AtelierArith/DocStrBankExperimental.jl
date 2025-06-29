```
XPRS_MIPABSCUTOFF
```

分岐限定法: ユーザーが目的関数の値がある値よりも良いものにのみ興味がある場合、これを `MIPABSCUTOFF` に割り当てることができます。(double)

これにより、最適化ツールは、より悪い目的値をもたらす可能性のあるノードの解決を無視でき、解決時間を節約します。MIPソリューションが見つかると、新しいカットオフ値が計算され、その値はCURRMIPCUTOFF属性から取得できます。CURRMIPCUTOFFの値は、`MIPRELCUTOFF` および `MIPADDCUTOFF` コントロールを使用して計算されます。

デフォルト値: `1.0E+40` (最小化問題の場合); `-1.0E+40` (最大化問題の場合)。

ドメイン: [-INF,+INF]
