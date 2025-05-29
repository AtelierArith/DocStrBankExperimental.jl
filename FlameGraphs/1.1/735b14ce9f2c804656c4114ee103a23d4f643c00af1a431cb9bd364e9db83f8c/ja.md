```
fcolor = FlameColors(n::Integer=2;
                     colorbg=colorant"white", colorfont=colorant"black",
                     colorsrt=colorant"crimson", colorsgc=colorant"orange")
```

フレームグラフを描画するための色のセットを選択します。いくつかの特別な色があります：

  * `colorbg` は背景色です
  * `colorfont` はスタックフレームにテキストを注釈する際に使用されます
  * `colorsrt` は [ランタイムディスパッチ](https://discourse.julialang.org/t/dynamic-dispatch/6963) を強調表示し、通常はコストのかかるプロセスです
  * `colorsgc` はガーベジコレクションイベントを強調表示します

`n` は、上記のいずれかが関連しない場合に選択する「その他」の色の数を指定します。`FlameColors` は `2n` 色を選択します：最初の `n` 色はスタックトレースの奇数深度用、最後の `n` 色はスタックトレースの偶数深度用です。したがって、異なるスタックフレームは通常、色によって区別可能です。

強調表示は、`colorsrt` または `colorsgc` に `nothing` またはゼロ要素のベクトルを渡すことで無効にできます。`colorsrt` または `colorsgc` に単一の色を渡すと、このメソッドは指定された色とはわずかに異なる4つのバリアント色を生成します。`colorsrt` または `colorsgc` は、ベクトルで複数の色として指定することもできます。ベクトルの前半は奇数深度用、後半は偶数深度用です。単一の色の代わりに1要素のベクトルを使用することで、指定された色が常に使用されます。

戻り値は `struct` ですが、呼び出し可能であり、`flamepixels` の `fcolor` 入力として使用できます。
