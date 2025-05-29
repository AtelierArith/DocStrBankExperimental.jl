```
grdgradient(cmd0::String="", arg1=nothing, kwargs...)
```

与えられた方向における方向微分を計算するか、データのベクトル勾配の方向[および大きさ]を見つけます。

完全なGMT（`GMT.jl`ではない）ドキュメントは[`grdgradient`](http://docs.generic-mapping-tools.org/latest/grdgradient.html)で確認できます。

## パラメータ

  * **A** | **azim** | **azimuth** :: [Type => Str | Number]    $Arg = azim[/azim2]$

    方向微分のための方位角。
  * **D** | **find_dir** :: [Type => Str]      $Arg = [a][c][o][n]$

    データの正の（上昇）勾配の方向を見つけます。
  * **G** | **save** | **write** | **outgrid** | **outfile** :: [Type => Str]

    出力グリッドファイル名。これはオプションであり、結果を直接ディスクに保存する場合のみ使用されます。それ以外の場合は、G = grdgradient(....)の形式を使用してください。
  * **E** | **lambert** :: [Type => Str]    $Arg = [m|s|p]azim/elev[+aambient][+ddiffuse][+pspecular][+sshine]$

    grdimageおよびgrdviewと一緒に使用するのに適したランバート放射を計算します。
  * **N** | **norm** | **normalize** :: [Type => Str]     $Arg = [e|t][amp][+ssigma][+ooffset]$

    正規化。[デフォルトは正規化なしです。] 実際の勾配gはオフセットされ、スケーリングされて正規化された勾配を生成します。
  * **Q** | **save_stats** :: [Type => Str]		$Arg = c|r|R$

    Nによる正規化がどのように行われるかを制御します。
  * **R** | **region** | **limits** :: [Type => Str or list or GMTgrid|image]	$Arg = (xmin,xmax,ymin,ymax)$

    興味のある領域を指定します。提供されていない場合はデータの最小バウンディングボックスに設定されます。
  * **S** | **slopegrid** :: [Type => Str]

    勾配ベクトルのスカラー大きさを持つ出力グリッドファイルの名前。Dが必要ですが、Gはオプションにします。
  * **V** | **verbose** :: [Type => Bool or Str]		$Arg = [level]$

    進捗報告をstderrに送信する冗長性レベルを選択します。
  * **f** | **geog** | **colinfo** | **coltypes** | **coltype** :: [Type => Str]        $Arg = [i|o]colinfo$

    入力および/または出力列のデータ型（時間または地理データ）を指定します。

完全なドキュメントを見るには、次のように入力してください: $@? grdgradient$
