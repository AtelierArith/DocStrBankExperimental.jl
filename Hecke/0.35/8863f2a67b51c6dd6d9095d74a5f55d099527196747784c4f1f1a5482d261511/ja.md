```
evaluate(x::FacElem{QQFieldElem}) -> QQFieldElem
evaluate(x::FacElem{ZZRingElem}) -> ZZRingElem
```

因子化された要素を展開または評価します。つまり、実際に要素を計算します。最初に互いに素な基底要素への冪積の簡略化されたバージョンを取得することによって機能します。
