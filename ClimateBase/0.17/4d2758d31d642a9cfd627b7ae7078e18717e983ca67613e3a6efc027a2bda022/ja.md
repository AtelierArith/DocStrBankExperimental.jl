```
sametimespan(Xs; mintime = nothing, maxtime = nothing) → Ys
```

`ClimArray`のコンテナを与えると、同じ`ClimArray`を返しますが、`Time`次元でアクセスされ、すべてが同じ時間間隔を持つようになります。値が`ClimArray`の辞書にも対応しています。

オプションで、キーワード`mintime, maxtime`に対して`Date`または`DateTime`の値を提供することで、アクセスされる最小/最大時間間隔をさらに制限できます。

`sametimespan`は、配列の時間的サンプリングを考慮して、より正確に処理します。
