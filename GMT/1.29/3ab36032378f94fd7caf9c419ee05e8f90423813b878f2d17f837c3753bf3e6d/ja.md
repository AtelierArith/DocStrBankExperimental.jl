```
gmtisf(cmd0::String; kwargs...)
```

ISF形式のファイルから地震データを読み込みます。

## パラメータ

  * **R** | **region** | **limits** :: [Type => Str or list or GMTgrid|image]	$Arg = (xmin,xmax,ymin,ymax)$

    興味のある地域を指定します。提供されていない場合はデータの最小バウンディングボックスに設定されます。
  * **D** | **date** :: date="datestart[/dateend]"

    出力をデータ >= datestart、または datestart と dateend の間に制限します。<date> は ISO 形式でなければなりません。例: 2000-04-25。
  * **F** | **focal** :: [Type => Bool or Str or Symbol]

    焦点メカニズムを持つイベントのみを選択します。デフォルトは Global CMT 規約です。AKI 規約を使用するには `focal=:a` を指定します。
  * **N** | **notime** :: [Type => Bool]

    時間情報を出力しません。
  * `abstime or unixtime` :: [Type => Integer]

    YYYY、MM、DD、HH、MM 列を unixtime に変換します。デフォルトでは最初の列に配置され、`abstime=2` を使用すると最後の列に配置されます。
  * **yx** :: [Type => Str or Bool or []]     $Arg = [i|o]$

    入力および/または出力で1列目と2列目を入れ替えます。

このモジュールは `gmtread` を介しても呼び出すことができます。*I.,e.* `gmtread("file.isf", opts...)_
