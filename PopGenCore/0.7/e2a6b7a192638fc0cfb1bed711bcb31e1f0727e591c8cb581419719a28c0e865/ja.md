```
PopGen.write(data::PopData, filename::String, kwargs...)
PopGen.write(data::PopData; filename::String, kwargs...)
```

指定されたファイルタイプに`PopData`を書き込みます。ファイル名の拡張子から推測されます（大文字と小文字は区別されません）。追加のキーワード引数`kwargs...`は、意図されたファイルタイプに特有のものであり、特定のファイルライターのドキュメントに`?filetype`の形式でリストされています。たとえば、Genepop形式への変換に適切なキーワードを見つけるには、`?genepop`ドキュメントを呼び出します。

| ファイル形式    | 拡張子                    | ドキュメント     |
|:--------- |:---------------------- |:---------- |
| genepop   | `.gen`, `.genepop`     | ?genepop   |
| delimited | `.csv`, `.txt`, `.tsv` | ?delimited |
| structure | `.str`, `.structure`   | ?structure |
| plink     | `.ped`                 | ?plink     |
| baypass   | `.baypass`             | ?baypass   |

### 例

```
cats = @nancycats;
fewer_cats = omit(cats, name = samplenames(cats)[1:10]);
PopGen.write(fewer_cats, filename = "filtered_nancycats.gen", digits = 3, format = "h")
```
