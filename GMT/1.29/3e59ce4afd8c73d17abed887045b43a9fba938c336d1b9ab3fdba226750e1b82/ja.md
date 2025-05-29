```
grdpaste(cmd0::String="", G1=nothing, G2=nothing, kwargs...)
```

グリッド $grid1$ と $grid2$ を共通のエッジに沿って一緒に貼り付けて $grid3$ に結合します。両方のグリッドは同じ dx、dy を持ち、共通のエッジを持っている必要があります。

完全な GMT ( `GMT.jl` ではなく) ドキュメントは [`grdpaste`](http://docs.generic-mapping-tools.org/latest/grdpaste.html) を参照してください。

## パラメータ

  * **G** | **save** | **outgrid** | **outfile** :: [Type => Str]

    出力グリッドファイル名。これはオプションであり、結果を直接ディスクに保存する場合のみ使用されます。それ以外の場合は、G = grdpaste(....) 形式を使用してください。
  * **V** | **verbose** :: [Type => Bool or Str]		$Arg = [level]$

    進行状況レポートを stderr に送信するための冗長性レベルを選択します。
  * **f** | **geog** | **colinfo** | **coltypes** | **coltype** :: [Type => Str]        $Arg = [i|o]colinfo$

    入力および/または出力列のデータタイプ（時間または地理データ）を指定します。

完全なドキュメントを見るには、次のように入力してください: $@? grdpaste$
