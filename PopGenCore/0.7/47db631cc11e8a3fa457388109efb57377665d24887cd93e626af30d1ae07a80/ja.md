```
PopGen.read(infile::String; kwargs...)
```

個々のファイルインポータをラップして、ファイルを `PopData` オブジェクトとして読み込みます。ファイルタイプはファイル拡張子から推測されます（大文字と小文字を区別しません）：

| ファイル形式               | 拡張子                    | ドキュメント       |
|:-------------------- |:---------------------- |:------------ |
| 区切り文字                | `.csv`, `.txt`, `.tsv` | `?delimited` |
| genepop              | `.gen`, `.genepop`     | `?genepop`   |
| 構造                   | `.str`, `.structure`   | `?structure` |
| plink                | `.bed`, `.ped`         | `?plink`     |
| バリアントコールフォーマット (vcf) | `.vcf`, `.vcf.gz`      | `?vcf`       |
| バリアントコールフォーマット (bcf) | `.bcf`, `.bcf.gz`      | `?bcf`       |

この関数は、ラップしているファイルインポート関数と同じキーワード引数（およびデフォルト）を使用します。特定の使用詳細については、Julia ヘルプコンソールでそれぞれのドキュメントを参照してください（例：`?genepop`）。

## 例

```
PopGen.read("cavernous_assfish.gen", digits = 3)

PopGen.read("juglans_nigra.vcf")
```
