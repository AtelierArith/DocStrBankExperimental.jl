`closure(fst; star=true)`

新しいWFST `cfst`を返します。これは`fst`の閉包です。もし`fst`が`labels`を`olabel`に重み`w`で変換する場合、`cfst`は任意の整数`n`に対して`repeat(ilabels,n)`を`repeat(olabels,m)`に重み`w^n`で変換できるようになります。

`star`が`true`の場合、`cfst`は空の文字列を重み1で自分自身に変換します。
