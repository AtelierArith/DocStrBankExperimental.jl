```
@with df begin
    # dfを使って何かをする
end
```

`@with`マクロは、現在のデータフレームを設定し、それに対して操作を単一のブロック内で実行するための便利なマクロです。最初の引数は現在のデータフレームとして設定するデータフレームであり、2番目の引数は実行するコードのブロックです。ブロックの期間中、データフレームは現在のデータフレームとして設定され、ブロックが実行された後に以前の値に復元されます。

マクロはブロック内の最後の式の値を返します。
