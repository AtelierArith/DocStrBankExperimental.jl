```
textonpoly(str, pgon;
        tracking = 0,
        startoffset = 0.0,
        baselineshift = 0.0,
        closed = false)
```

`pgon`のポリゴンのルートに沿って`str`のテキストを描画します。

`closed`オプションは、ポリゴンの最終辺（最後の点を最初の点に結ぶ）が含まれるかどうかを決定します。例えば、三角形の3つの辺の周りに文字列を描画したい場合は、`closed=true`を使用します：

```julia
textonpoly("mèdeis ageômetrètos eisitô mou tèn
stegèn - let no one ignorant of geometry come under my roof
",
    ngon(O, 100, 3, vertices=true),
    closed=true)
```

`false`の場合、2つの辺のみが考慮されます。

`tracking`を0から増やすことで、グリフ間のスペースを追加します。

`startoffset`の値は、開始位置を指定する正規化されたパーセンテージです。したがって、ポリゴンの途中からテキストの描画を開始するには、開始オフセット値を0.5に指定します。

`baselineshift`の正の値は、文字をベースラインから上に移動させます。

描画された文字の数と、0.0から1.0の間のインデックスの最終値を含むタプルを返します。返されたインデックス値が1未満の場合、これは提供されたテキストがポリゴンの終わりに達する前に尽きたことを意味します。
