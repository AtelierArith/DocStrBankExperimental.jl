```
recycle!(list::MoveList)
```

ムーブリストを再利用して新しいムーブを生成するために再利用します。

これは、ヒープメモリを過剰に割り当てるのを避けたい場合に便利です。もはや必要のない `MoveList` がある場合は、次回ムーブを生成する必要があるときに新しいものを作成する代わりに再利用することを検討してください。
