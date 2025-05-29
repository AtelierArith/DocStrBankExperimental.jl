```
unloadFMU(fmu::FMU2, cleanUp::Bool=true; secure_pointers::Bool=true)
```

FMUをアンロードします。割り当てられたメモリを解放し、バイナリを閉じ、一時的なzipおよび解凍されたFMUモデルの説明を削除します。

# 引数

  * `fmu::FMU2`: FMI 2.0.2標準におけるFMUとそのすべてのインスタンスを表す可変構造体。
  * `cleanUp::Bool= true`: ファイルとディレクトリを削除するかどうかを定義します。

# キーワード

  * `secure_pointers=true` C関数へのポインタをダミーで上書きするかどうか（遅くなるが、ユーザーにとって安全性が高い）
