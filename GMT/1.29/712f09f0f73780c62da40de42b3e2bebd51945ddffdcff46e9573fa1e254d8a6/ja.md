```
gmtset(; kwargs...)
```

現在のディレクトリの gmt.conf ファイルで個々の GMT デフォルト設定を調整します。

完全な GMT ( `GMT.jl` ではなく) ドキュメントは [`gmtset`](http://docs.generic-mapping-tools.org/latest/gmtset.html) を参照してください。

## パラメータ

  * **D** | **units** :: [Type => Str | []]

    システム設定に基づいて GMT デフォルトを変更します。US デフォルトには u を、SI デフォルトには s を追加します。
  * **G** | **defaultsfile** :: [Type => Str]

    読み取りおよび変更する特定の gmt.conf ファイルの名前。
  * **V** | **verbose** :: [Type => Bool or Str]		$Arg = [level]$

    進行状況レポートを stderr に送信する冗長性レベルを選択します。
  * **write** | **|>** :: [Type => Str]     $Arg = fname$

    結果を Julia 変数に戻すのではなく、ASCII ファイルに保存します。ファイル名を引数として指定します。バイナリファイルとして保存するには bo オプションを使用します。

### 例:

```
gmtset(FONT_ANNOT_PRIMARY="12p,Helvetica", MAP_GRID_CROSS_SIZE_PRIMARY=0.25)
```
