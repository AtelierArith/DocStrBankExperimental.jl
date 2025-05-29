```
FaceField(data, grid)
```

`grid`上に`data`が配置された`FaceField`を返します。もし`data`が`FaceField`の*合計*サイズと同じであれば、`data`は`OffsetArray`にラップされます。そうでない場合、`data`は`size(grid)`の`FaceField`に設定可能でなければなりません。
