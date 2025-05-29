```
ellipse(focus1::Point, focus2::Point, k;
        action=:none,
        stepvalue=pi/100,
        vertices=false,
        reversepath=false)
```

2つの点と距離 `k` を指定して楕円の多角形近似を構築します。ここで、`k` は楕円上の任意の点から焦点までの距離の合計（または、1つの焦点から周囲まで、そしてもう1つの焦点まで行くのに必要な最短の糸の長さ）です。そして、それを現在のパスに追加します。
