```
gmtwhich(cmd0::String; kwargs...)
```

指定されたファイルのフルパスを見つける

完全なGMT（`GMT.jl`ではない）ドキュメントは[`gmtwhich`](http://docs.generic-mapping-tools.org/latest/gmtwhich.html)を参照してください。

## パラメータ

  * **A** | **readable** :: [Type => Bool]

```
ユーザーが読み取る権限を持つファイルのみを考慮します [デフォルトは見つかったすべてのファイルを考慮]。
```

  * **C** | **confirm** :: [Type => Bool]

```
パスを報告する代わりに、ファイルが見つかった場合は確認のYを、見つからなかった場合はNを印刷します。
```

  * **D** | **report_dir** :: [Type => Bool]

```
パスを報告する代わりに、ファイルを含むディレクトリを印刷します。
```

  * **G** | **download** :: [Type => Str | []]      $Arg = [c|l|u]$

```
ファイル引数がダウンロード可能なファイル（完全なURL、GMTサイトキャッシュからダウンロードするための@file、または@earth_relief_*.grd）である場合、ローカルデータまたはキャッシュディレクトリに見つからない場合はファイルをダウンロードしようとします。
```

  * **V** | **verbose** :: [Type => Bool or Str]		$Arg = [level]$

    進捗レポートをstderrに送信する冗長性レベルを選択します。
