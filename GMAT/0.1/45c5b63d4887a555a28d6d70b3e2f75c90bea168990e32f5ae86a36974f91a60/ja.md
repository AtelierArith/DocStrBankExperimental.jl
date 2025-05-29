```
run_script(script;
	data=joinpath(artifact"data", "gmat-data-2020a"),
	output=joinpath(pwd(), "gmat-output"),
)
```

GMAT `script`を実行し、オプションで`data`パッケージへのパスと`output`ディレクトリを指定します。この関数は出力ファイルのリストを返します。

### 参考文献

  * [GMAT Documentation](http://gmat.sourceforge.net/docs/R2020a/html/index.html)
