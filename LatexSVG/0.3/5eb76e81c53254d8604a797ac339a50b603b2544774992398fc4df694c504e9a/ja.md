```
Lsvg"..."
```

現在の前文とLaTeXエンジンを使用して、入力をSVGとしてレンダリングします。

`raw"..."`文字列と同様に、`\`や`$`のような特殊文字をエスケープする必要がないため、LaTeXを書くのが簡単になります。

変数を`%$`構文を使用して補間することができ、これは`LaTeXStrings.jl`の`L"..."`文字列マクロと同じです。たとえば、変数`x = 10`がある場合、`Lsvg"number %$x"`は文字列`"number 10"`をレンダリングします。ただし、`L"..."`マクロとは異なり、`Lsvg"..."`は自動的に入力をドル記号のペアで囲むことはありません。これは、他のLaTeX環境を使用したい場合があるためです。
