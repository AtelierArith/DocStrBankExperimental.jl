```
showfig([fmt="format", figname="figname[.fmt]"])
```

PostScriptファイルを完成させ、図を変換して表示します。

  * `fmt`: フォーマット `format` でラスタ図を作成します。デフォルトは `fmt=:png` です。PDF形式で取得するには `fmt=:pdf` とします。
  * `figname`: ローカルディレクトリに図を作成し、名前を `figname` にします。`figname` に拡張子がある場合、それが図のフォーマットを選択するために使用されます。*例* `figname=fig.pdf` は、ローカルに 'fig.pdf' というPDFファイルを作成します。
