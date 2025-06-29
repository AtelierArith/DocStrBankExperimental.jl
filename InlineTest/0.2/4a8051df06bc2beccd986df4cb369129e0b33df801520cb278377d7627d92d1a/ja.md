```
@testset args...
```

`Test.@testset args...` と似ていますが、含まれるテストはすぐには実行されず、代わりに後で実行するために保存されます。これは [`retest()`](@ref) または `runtests()` によってトリガーされます。

`@testset` の本体（最後の引数）と説明文字列の他に、`@testset` の引数には以下が含まれます：

  * *リテラル* ブール値を持つ `verbose` オプション（例： `verbose=true`）
  * テストセットのフィルタリングに使用できるラベルとして機能するリテラルシンボル（詳細は [`retest`](@ref) のドキュメントを参照）。すべてのネストされたテストセットはそのようなラベルを継承します。

`@testset` の呼び出しはネスト可能ですが、`ReTest.@testset` の修飾された呼び出しはできません。

内部的に、`@testset` の式は実行時に `Test.@testset` の同等物に変換されます。
