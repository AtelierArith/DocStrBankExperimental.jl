```
grdfft(cmd0::String="", arg1=nothing, [arg2=nothing,] kwargs...)
```

2次元の前方高速フーリエ変換を行い、空間領域に戻す前に周波数領域で1つ以上の数学的操作を実行します。

完全なGMT（`GMT.jl`ではない）ドキュメントは[`grdfft`](http://docs.generic-mapping-tools.org/latest/grdfft.html)を参照してください。

## パラメータ

  * **A** | **azim** :: [Type => Number]    $Arg = azim$

    北から時計回りに度で測定された方位方向の方向微分を取ります。
  * **C** | **upward** :: [Type => Number]    $Arg = zlevel$

    上方（zlevel > 0の場合）または下方（zlevel < 0の場合）にフィールドをzlevelメートル続けます。
  * **D** | **dfdz** :: [Type => Str or Number]		$Arg = [scale|g]$

    フィールドを微分します。すなわち、d(field)/dzを取ります。これは周波数領域でkr（krは放射波数）を掛けることに相当します。
  * **E** | **radial_power** :: [Type => Str]         $Arg = [r|x|y][+w[k]][+n]$

    放射方向[r]でパワースペクトルを推定します。Eの後にxまたはyをすぐに置くことで、xまたはy方向のスペクトルを計算します。
  * **F** | **filter** :: [Type => Str or List–        $Arg = [r|x|y]params$

    データをフィルタリングします。-Fの後にxまたはyをすぐに置くことで、xまたはy方向のみをフィルタリングします。デフォルトは等方的[r]です。コサインテーパー付きバンドパス、ガウスバンドパスフィルタ、またはバターワースバンドパスフィルタのいずれかを選択します。
  * **G** | **save** | **outgrid** | **outfile** :: [Type => Str]

    出力グリッドファイル名（または**radial_power**が使用される場合はテーブル）。これはオプションであり、結果を直接ディスクに保存する場合のみ使用されます。それ以外の場合は、G = grdfft(....)の形式を使用してください。
  * **I** | **integrate** :: [Type => Str or Number]		$Arg = [scale|g]$

    フィールドを積分します。すなわち、積分*over*z（フィールド * dz）を計算します。これは周波数領域でkr（krは放射波数）で割ることに相当します。
  * **N** | **inquire** :: [Type => Str]         $Arg = [a|f|m|r|s|nx/ny][+a|[+d|h|l][+e|n|m][+twidth][+v][+w[suffix]][+z[p]]$

    FFTに適したグリッド次元を選択または問い合わせ、オプションのパラメータを設定します。FFT次元を制御します：
  * **S** | **scale** :: [Type => Number]			$Arg = scale$

    周波数領域の操作の後に空間領域で各要素にスケールを掛けます。
  * **V** | **verbose** :: [Type => Bool or Str]		$Arg = [level]$

    進行状況レポートをstderrに送信する冗長性レベルを選択します。
  * **f** | **geog** | **colinfo** | **coltypes** | **coltype** :: [Type => Str]        $Arg = [i|o]colinfo$

    入力および/または出力列のデータ型（時間または地理データ）を指定します。
