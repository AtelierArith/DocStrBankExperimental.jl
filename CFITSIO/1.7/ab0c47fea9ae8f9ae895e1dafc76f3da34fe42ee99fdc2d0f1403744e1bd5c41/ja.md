```
fits_copy_file(fin::FITSFile, fout::FITSFile, previous::Bool, current::Bool, following::Bool)
```

入力ファイル `fin` から HDU のすべてまたは一部をコピーし、出力ファイル `fout` に追加します。フラグ `previous`、`current`、`following` は、どの HDU をコピーするかを指定します。

  * `previous` が true の場合、現在の入力 HDU の前のすべての HDU がコピーされます。
  * `current` が true の場合、現在の入力 HDU がコピーされます。
  * `following` が true の場合、現在の入力 HDU の後のすべての HDU がコピーされます。

これらのフラグは組み合わせることができるため、すべてが true に設定されている場合、すべての HDU が `fin` から `fout` にコピーされます。

終了時に、入力は変更されず、出力の最後の HDU が現在の HDU として設定されます。
