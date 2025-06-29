```
filereader(path; [...])
```

`Julia`に区切り文字付きファイルを読み込みます。

# キーワード引数

  * `types`: ユーザーは、`types`キーワード引数を使用して入力ファイルの各列の型を渡すことができます。ユーザーは、各列のすべての型を含む型のベクトルを渡すことも、いくつかの選択された列の型の辞書を渡すこともできます。
  * `delimiter`: デフォルトの区切り文字を変更するには、ユーザーは`delimiter`キーワード引数を渡す必要があります。`delimiter`キーワード引数は、区切り文字として`Char`のみを受け入れます。さらに、ユーザーは`Char`のベクトルを渡すことができ、これにより`filereader`はそれらを代替の区切り文字として使用します。
  * `dlmstr`: このキーワード引数は、値の区切り文字として文字列を渡すために使用されます。
  * `ignorerepeated`: `true`に設定されている場合、繰り返しの区切り文字は無視されます。
  * `header`: 入力ファイルの最初の行が列のヘッダーでない場合、ユーザーはこれを`false`に設定する必要があります。さらに、ユーザーは列名のベクトルを渡すことができ、これが列のヘッダーとして使用されます。
  * `linebreak`: `filereader`関数は、このオプションの値を行の区切り文字として使用します。`Char`または長さが2以下の`Char`のベクトルを受け入れることができます。稀なケースでは、ユーザーはこのオプションを渡して`filereader`が入力ファイルを読み取るのを支援する必要があるかもしれません。
  * `guessingrows`: 型検出に使用される行数を提供します。ユーザーがこの値を増やすと、`filereader`関数は列の型をより正確に検出しますが、計算時間が増加します。
  * `fixed`: このオプションは、固定幅ファイルを読み取るために使用されます。ユーザーは、固定幅ファイルを読み取るための列の位置（範囲として）を含む辞書を渡す必要があります。
  * `quotechar`: 入力ファイル内のテキストが引用されている場合、ユーザーはこのキーワード引数を介して引用された文字を渡す必要があります。
  * `escapechar`: 引用されたテキストのエスケープ文字を宣言します。
  * `dtformat`: ユーザーは、DateTime列の標準形式と異なる場合、日付形式を渡す必要があります。`dtformat`キーワード引数は、値の辞書を受け入れます。
  * `int_base`: `filereader`は、指定された基数で整数を読み取ることができます。ユーザーは特定の列のためにこの情報を渡す必要があります。
  * `informat`: ユーザーは、選択された列の`informat`の情報を提供する辞書を渡すことができます。
  * `skipto`: 特定の位置からファイルの読み取りを開始するために使用できます。
  * `limit`: 入力ファイルから読み取る観測値の数を制限するために使用できます。
  * `multiple_obs`: `true`に設定されている場合、`filereader`関数は、入力ファイルの各行に複数の観測値があると仮定します。
  * `line_informat`: ユーザーはこのキーワード引数を介して行の情報を提供できます。
  * `buffsize`: ユーザーはバッファサイズのために任意の正の数を提供できます。各スレッドは`buffsize`の量を割り当て、入力ファイルから値を読み取ります。
  * `lsize`: 入力ファイルを読み取るための行バッファサイズを示します。非常に広いテーブルの場合、ユーザーはこのオプションを手動で調整する必要があるかもしれません。その値は`buffsize`より小さくなければなりません。
  * `string_trim`: これを`true`に設定すると、出力データセットに保存する前に文字列の末尾の空白がトリムされます。
  * `makeunique`: 非一意の列名がある場合、これにより名前にサフィックスを追加することで解決できます。
  * `emptycolname`: `true`に設定されている場合、空の名前の列に対して列名が生成されます。
  * `warn`: 警告と情報の最大数を制御します。これを0に設定すると、入力ファイルの読み取り中に警告と情報が抑制されます。
  * `eolwarn`: 行末文字の警告を表示するかどうかを制御します。
  * `threads`: 大きなファイルの場合、`filereader`関数はすべてのスレッドを利用します。ただし、この引数を`false`に設定することでオフにすることができます。
  * `threshold`: 高性能アルゴリズムに切り替えるための最小ファイルサイズを指定するファイルサイズの閾値（バイト単位）。デフォルトでは2^26に設定されています。
