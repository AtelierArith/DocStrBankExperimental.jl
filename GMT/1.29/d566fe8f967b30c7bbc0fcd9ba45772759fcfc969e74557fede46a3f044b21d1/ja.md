```
grdedit(cmd0::String="", arg1=nothing, kwargs...)
```

バイナリ2-Dグリッドファイルのヘッダー情報を読み取り、コマンドラインで提供された値で情報を置き換えます。

単一の入力がG GMTgridオブジェクトである場合、G.rangeメンバーのz_min|max値を更新します。

完全なGMT（`GMT.jl`ではない）ドキュメントは[`grdedit`](http://docs.generic-mapping-tools.org/latest/grdedit.html)を参照してください。

## パラメータ

  * **A** | **adjust_inc** :: [Type => Bool]

    必要に応じて、ファイルのx*inc、y*incをそのドメインと互換性があるように調整します。
  * **C** | **adjust_inc** :: [Type => Bool]

    グリッドヘッダーからコマンド履歴をクリアします。
  * **D** | **header** | **metadata** :: [Type => Str]    $Arg = [+xxname][+yyname][+zzname][+sscale][+ooffset][+ninvalid][+ttitle][+rremark$

    これらのヘッダーパラメータを変更します。
  * **E** | **flip** :: [Type => Str]    $Arg = [a|h|l|r|t|v]$

    グリッドを6つの方法のいずれかで変換し、（l|r|tの場合）xとyの情報を入れ替えます。
  * **G** | **save** | **outgrid** | **outfile** :: [Type => Str]

    出力グリッドファイル名。これはオプションであり、結果を直接ディスクに保存する場合のみ使用されます。それ以外の場合は、G = grdedit(....)形式を使用してください。
  * **J** | **proj** | **projection** :: [Type => String]

    地図投影を選択します。デフォルトは15x10 cmの線形（非投影）マップです。
  * **N** | **replace** :: [Type => Str | Mx3 array]      $Arg = replace=fname | replace=Array$

    ASCII（またはバイナリ）ファイルテーブルを読み取り、グリッド内の対応するノード値をこれらのx,y,z値で置き換えます。あるいは、変更する値を持つMx3行列を提供します。
  * **R** | **region** | **limits** :: [Type => Str or list or GMTgrid|image]	$Arg = (xmin,xmax,ymin,ymax)$

    興味のある領域を指定します。提供されていない場合は、データの最小バウンディングボックスに設定されます。
  * **S** | **wrap** :: [Type => Bool]

    グローバルな地理グリッドのみ。グリッド値は、$limits$（Rオプション）で指定された新しい境界に従って経度方向にシフトされます。
  * **T** | **toggle_reg** | **toggle** :: [Type => Bool]

    グリッドライン登録グリッドをピクセル登録グリッドに変換するために、ヘッダーに必要な変更を行います。
  * **V** | **verbose** :: [Type => Bool or Str]		$Arg = [level]$

    進行状況レポートをstderrに送信する冗長性レベルを選択します。
  * **bi** | **binary_in** :: [Type => Str]			$Arg = [ncols][type][w][+L|+B]$

    プライマリ入力のネイティブバイナリ形式を選択します（セカンダリ入力は常にASCIIです）。
  * **di** | **nodata_in** :: [Type => Str or Number]      $Arg = nodata$

    すべての入力列を調べ、任意の項目がnodataに等しい場合、この値を欠損データ項目として解釈し、値NaNに置き換えます。
  * **e** | **pattern** | **find** :: [Type => Str]        $Arg = [~]”pattern” | -e[~]/regexp/[i]$

    指定されたパターンを含むASCIIデータレコードのみを受け入れます。
  * **f** | **geog** | **colinfo** | **coltypes** | **coltype** :: [Type => Str]        $Arg = [i|o]colinfo$

    入力および/または出力列のデータ型（時間または地理データ）を指定します。
  * **yx** :: [Type => Str or Bool or []]     $Arg = [i|o]$

    入力および/または出力で1列目と2列目を入れ替えます。

```
