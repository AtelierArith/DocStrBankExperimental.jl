```
extrapolate(fh_itr; power=1,
                    atol=0, rtol=0, maxeval=typemax(Int), breaktol=Inf)
```

`extrapolate(f, h)`と同様に、値のシーケンス`f(h)`のリチャードソン外挿を`h → 0`に対して行いますが、`(f(h), h)`のタプルのシーケンスのイテラブルコレクション`fh_itr`を受け取ります（`|h|`が減少する順序で）。

収束因子は`h`の値のシーケンスによって決定されるため、`contract`キーワード引数はありません（同じ量だけ収束する必要はありません）。許容誤差`atol`と`rtol`はどちらもデフォルトで`0`に設定されているため、デフォルトでは`fh_itr`コレクション内の*すべて*の値を調べます。それ以外の場合、キーワード引数は`extrapolate(f, h)`と同じ意味を持ちます。
