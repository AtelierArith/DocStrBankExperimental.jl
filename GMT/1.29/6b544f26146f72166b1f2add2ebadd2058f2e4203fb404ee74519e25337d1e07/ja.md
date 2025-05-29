```
gmt2kml(cmd0::String="", arg1=nothing, kwargs...)
```

Google Earth用のKMLファイルにGMTデータテーブルを変換します

## パラメータ

  * **A** | **altitude_mode** :: [Type => Str]       $Arg = a|g|s[alt|xscale]$

    Google Earthによって認識される3つの高度モードのいずれかを選択します。これは、特徴の高度（m単位）を決定します：$a$ 絶対高度、$g$ 海面または地面に対する相対高度、$s$ 海底または地面に対する相対高度です。
  * **C** | **color** | **colormap** | **cmap** | **colorscale** :: [Type => Str]	$Arg = [cpt |master[+izinc] |color1,color2[,*color3*,…]]$

    CPT名を指定するか、-Ccolor1,color2[,color3,...]を指定して、これらの色から自動的に線形連続CPTを構築します。
  * **D** | **descript** :: [Type => Str]   $Arg = descriptfile$

    KMLファイルの主要な説明コンテンツの一部として含まれるHTMLスニペットを含むファイルです。
  * **E** | **extrude** :: [Type => Str | []]  $Arg = [altitude]$

    特徴を地面レベルまで押し出します。
  * **F** | **feature_type** :: [Type => Str]  $Arg = e|s|t|l|p|w$

    特徴のタイプを設定します。ポイント（イベント、シンボル、またはタイムスパン）、ライン、ポリゴン、またはウィグルから選択します。
  * **G** | **fill** :: [Type => Str]  $Arg = f|nfill$

    色の塗りつぶし（G=:f）またはラベルフォントの色（G=:n）を設定します。
  * **I** | **icon** :: [Type => Str]      $Arg = icon$

    シンボルに使用する代替アイコンのURLを指定します [デフォルトはGoogle Earthの円です]。
  * **K** | **not_over** :: [Type => Bool]

    後で出力に追加のKMLコードを付加できるようにします [KMLファイルを最終化します]。
  * **L** | **extra_data** :: [Type => Str]      $Arg = name1,name2,…$

    拡張データが与えられます。カンマで区切られた1つ以上の列名を追加します。
  * **N** | **feature_name** :: [Type => Str | Number]      $Arg = [t|col |name_template|name]$

    デフォルトでは、セグメントヘッダーに -L”label string”が含まれている場合、それをKML特徴の名前として使用します。
  * **O** | **overlay** :: [Type => Bool]

    既存のKMLファイルにKMLコードを追加します [新しいKMLファイルを初期化します]。
  * **Qa** | **wiggles** :: [Type => Str]      $Arg =  azimuth$

    ウィグルプロットをサポートするオプション（F=:wが必要です）。
  * **Qs** | **wiggle_scale** :: [Type => Str | Number]      $Arg =  scale[unit]$

    ウィグルプロットに必要な設定（つまり、F=:wが必要です）。ユーザーの単位に対するzデータ単位でウィグルスケールを設定します。
  * **R** | **region** | **limits** :: [Type => Str or list or GMTgrid|image]	$Arg = (xmin,xmax,ymin,ymax)$

    興味のある地域を指定します。提供されていない場合はデータの最小バウンディングボックスに設定します。
  * **S** | **ilscale** :: [Type => Str]      $Arg =  c|nscale$

    アイコンまたはラベルをスケーリングします。ここで、S=:cはシンボルアイコンのスケールを設定し、S=:nは名前ラベルのスケールを設定します。
  * **T** | **title** :: [Type => Str]    $Arg = title[/foldername]$

    ドキュメントのタイトルを設定します [デフォルトは未設定です]。オプションで、/FolderNameを追加します。
  * **W** | **pen** :: [Type => Str | []]      $Arg =  [pen][attr]$

    ライン、ウィグル、またはポリゴンのアウトラインのペン属性を設定します。
  * **Z** | **attrib** :: [Type => Str]      $Arg =  args$

    ドキュメントおよび地域タグの1つ以上の属性を設定します。
  * **V** | **verbose** :: [Type => Bool or Str]		$Arg = [level]$

    進捗レポートをstderrに送信する冗長性レベルを選択します。
  * **write** | **|>** :: [Type => Str]     $Arg = fname$

    結果をJulia変数に戻すのではなく、ASCIIファイルに保存します。ファイル名を引数として指定します。boオプションを使用してバイナリファイルとして保存します。
  * **append** :: [Type => Str]     $Arg = fname$

    結果をJulia変数に戻すのではなく、$fname$という名前の既存のファイルに追加します。boオプションを使用してバイナリファイルとして保存します。

完全なドキュメントを見るには、次のように入力します: $@? gmt2kml$
