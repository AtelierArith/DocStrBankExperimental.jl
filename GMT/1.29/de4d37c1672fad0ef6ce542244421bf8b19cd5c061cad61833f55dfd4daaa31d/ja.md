```
grdclip(cmd0::String="", arg1=nothing; kwargs...)
```

グリッド値の範囲をクリップします。低い値を下に、または高い値を上に設定します。また、すべての値を$between$に設定する1つ以上の区間を指定するか、個々の値を置き換えることもできます。

完全なGMT（`GMT.jl`ではない）ドキュメントは[`grdclip`](http://docs.generic-mapping-tools.org/latest/grdclip.html)を参照してください。

## パラメータ

  * **cmd0** :: [Type => Str]

    入力ファイル名。$arg1$引数を介してグリッド（GMTgridタイプ）が渡される場合は使用しないでください。
  * **G** | **save** | **outgrid** | **outfile** :: [Type => Str]

    出力グリッドファイル名。これはオプションであり、結果を直接ディスクに保存する場合のみ使用されます。それ以外の場合は、G = grdclip(....)形式を使用してください。
  * **R** | **region** | **limits** :: [Type => Str or list or GMTgrid|image]	$Arg = (xmin,xmax,ymin,ymax)$

    興味のある領域を指定します。提供されていない場合はデータの最小バウンディングボックスに設定されます。
  * **above** | **high** :: [Type => Array | Str]

    $$
    high
    $$

    と$above$の2要素配列、または"high/above"の文字列。すべてのdata[i] > $high$を$above$に設定します。
  * **below** | **low** :: [Type => Array | Str]

    $$
    low
    $$

    と$below$の2要素配列、または"low/below"の文字列。すべてのdata[i] < $low$を$below$に設定します。
  * **between** :: [Type => Array | Str]

    $$
    low, high
    $$

    と$between$の3要素配列、または"low/high/between"の文字列。すべてのdata[i] >= $low$および<= $high$を$between$に設定します。
  * **old** | **new** :: [Type => Array | Str]

    $$
    old
    $$

    と$new$の2要素配列、または"old/new"の文字列。すべてのdata[i] == $old$を$new$に設定します。
  * **S** :: [Type => Str]

    上記のすべての置換オプションを1つの文字列に圧縮します。
  * **V** | **verbose** :: [Type => Bool or Str]		$Arg = [level]$

    進行状況レポートをstderrに送信する冗長性レベルを選択します。
  * 例:

    ```
      G=gmt("grdmath", "-R0/10/0/10 -I1 X");
      G2=grdclip(G, above=[5 6], low=[2 2], between="3/4/3.5")
    ```

    または（オプションの2番目に-Sを使用することに注意してください。kwarg名を繰り返すことはできません）

    ```
      G2=grdclip(G, S="a5/6 -Sb2/2 -Si3/4/3.5")
    ```
