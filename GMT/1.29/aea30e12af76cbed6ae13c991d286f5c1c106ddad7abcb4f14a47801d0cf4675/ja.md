```
gmtinfo(cmd0::String="", arg1=nothing; kwargs...)
```

ファイルを読み込み、各列の極値を見つけます。

## パラメータ

  * **A** | **ranges** :: [Type => Str]

    範囲がどのように報告されるべきかを指定します。
  * **C** | **numeric** | **per_column** :: [Type => Bool]

    列ごとに最小/最大値を別々の列で報告します [デフォルトは<min/max>形式を使用]。
  * **D** | **center** :: [Type => Bool]

    -Iによって得られた結果を修正し、データの中心によりよく整列させるために領域をシフトします。
  * **E** | **get_record** :: [Type => Str | []]

    列colが最小(l)または最大(h)値を含むレコードを返します。
  * **F** | **counts** :: [Type => Str | []]

    追加されたモードに応じてさまざまなレコードのカウントを返します。
  * **I** | **inc** | **increment** | **spacing** :: [Type => Str | Number | Tuple]

    最初のn列の最小/最大を提供された増分の最も近い倍数に報告し、結果を-Rw/e/s/n形式で出力します。
  * **L** | **common_limits** :: [Type => Bool]

    テーブルやセグメント間の共通の制限を決定します。
  * **S** | **for*error*bars** :: [Type => Str | []]

    エラーバーのための追加のスペースを追加します。Iオプションと一緒に使用するのに便利で、後で`plot E`でプロットする際に役立ちます。
  * **T** | **nearest_multiple** :: [Type => Str | Number]    $Arg = dz[+ccol]$

    最初の(0’th)列の最小/最大をdzの最も近い倍数に報告し、これを文字列-Tzmin/zmax/dzとして出力します。
  * **V** | **verbose** :: [Type => Bool or Str]		$Arg = [level]$

    進行状況レポートをstderrに送信する冗長性レベルを選択します。
  * **write** | **|>** :: [Type => Str]     $Arg = fname$

    結果をJulia変数に戻すのではなく、ASCIIファイルに保存します。ファイル名を引数として指定します。boオプションを使用してバイナリファイルとして保存します。
  * **append** :: [Type => Str]     $Arg = fname$

    結果をJulia変数に戻すのではなく、$fname$という名前の既存のファイルに追加します。boオプションを使用してバイナリファイルとして保存します。

完全なドキュメントを見るには、次のように入力します: $@? grdmask$
