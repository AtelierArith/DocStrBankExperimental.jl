`authlist`から`s`の検証された文字列を返します。文字列は次の条件を満たす場合に有効と見なされます。

1. 小文字の値が略語の辞書のキー値として存在する
2. 小文字の値が権限リスト内のアイテムのユニークな開始値である
3. 小文字の値が指定されたLevenshtein編集距離の閾値内で権限リストのアイテムと一致する

```julia
validatedform(s, authlist; abbrdict, threshhold)

```
