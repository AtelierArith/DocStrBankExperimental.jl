```
@.. [thread=false] [broadcast=false] expr
```

`@..` は `expr` を `@.` に似たブロードキャストのような式に変換します。さらに、2つのオプションのキーワード引数を提供します：

  * thread: デフォルトは `false`。マルチスレッドを使用しますか？
  * broadcast: デフォルトは `false`。`true` の場合、動的なランタイムサイズが `1` の軸を大きなサイズにブロードキャストします。`false` の場合、コンパイル時に `1` であることが知られているサイズのみがサポートされます。つまり、`ArrayInterface.known_length(typeof(StaticArrayInterface.static_axes(x,i))) == 1` である軸はブロードキャストされます。これは、基本のブロードキャストとは異なることに注意してください。基本のブロードキャストは `broadcast=true` のみをサポートします。
