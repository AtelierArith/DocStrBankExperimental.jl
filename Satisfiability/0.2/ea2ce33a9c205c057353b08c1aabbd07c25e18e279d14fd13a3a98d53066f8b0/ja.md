```
save(z1, z2,..., io=open("out.smt", "w"))
save(z1, z2,..., io=open("out.smt", "w", line_ending='
```

', start*commands=nothing, end*commands=nothing)

`z`または`and(z1,...,zn)`のSMT表現をIOオブジェクトに書き込みます。キーワード引数:

  * `io`は、書き込み用に開かれたファイルなどのJulia IOオブジェクトです。
  * `line_ending`は行末文字を設定します。指定しない場合、Windowsシステムではデフォルトが`

`で、その他の場所では` `になります。

  * `start_commands`は`smt(z)`の前に挿入されます。通常、これを使用して`(set-info ...)`や`(set-option ...)`ステートメントを含めます。
  * `end_commands`は`(check-sat)`の後に挿入されます。これは、問題が充足可能かどうかをすでに知っている場合を除いて、あまり役に立たない傾向があります。

```
