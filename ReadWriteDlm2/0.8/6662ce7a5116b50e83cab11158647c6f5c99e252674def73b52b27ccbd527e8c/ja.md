## ReadWriteDlm2

`ReadWriteDlm2` 関数 `readdlm2()`, `writedlm2()`, `readcsv2()` および `writecsv2()` は stdlib.DelimitedFiles のものに似ていますが、`Date`, `DateTime`, `Time`, `Complex`, `Rational`, `Missing` 型および特別な小数点記号の追加サポートがあります。 `ReadWriteDlm2` は `Tables` インターフェースをサポートしています。

### `readcsv2(), writecsv2()`:

「小数点ドット」ユーザー向けに、関数 `readcsv2()` と `writecsv2()` はそれぞれ次のデフォルトを持っています: 区切り文字は `','`（固定）で、小数点は `'.'` です。

### `readdlm2(), writedlm2()`:

これらの関数の基本的なアイデアは「小数点コンマ国」をサポートすることです。デフォルトの区切り文字として `';'` を使用し、デフォルトの小数点記号として `','` を使用します。これらの関数の「小数点ドット」ユーザーは `decimal='.'` を定義する必要があります。

### 詳細なドキュメント:

機能や（キーワード）引数についての詳細は、`readdlm2()`, `writedlm2()`, `readcsv2()` および `writecsv2()` の `?help` を参照してください。
