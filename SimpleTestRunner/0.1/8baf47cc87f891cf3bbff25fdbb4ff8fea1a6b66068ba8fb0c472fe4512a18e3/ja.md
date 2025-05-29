```
testprogram()
```

テストプログラムファイルを特定します。

インタラクティブセッションの場合、または `PROGRAM_FILE` が空の場合、プログラムファイルは `testprogram()` の呼び出し元から呼び出されたファイルです。それ以外の場合、プログラムファイルは `PROGRAM_FILE` の値です。

例えば、`test/runtests.jl` が `runtests` を呼び出し、その後 `runtests` が `testprogram` を呼び出す場合：

  * インタラクティブセッションでは、プログラムファイルは `test/runtests.jl` です。
  * `PROGRAM_FILE` が空の場合、プログラムファイルは `test/runtests.jl` です。
  * 非インタラクティブセッションで `PROGRAM_FILE` が空でない場合、プログラムファイルは `PROGRAM_FILE` の値です。
