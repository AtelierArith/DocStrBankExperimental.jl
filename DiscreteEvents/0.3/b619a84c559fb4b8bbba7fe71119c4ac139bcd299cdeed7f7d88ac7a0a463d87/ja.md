```
sync!(clk::Clock, to::Clock=𝐶)
```

二つの時計を強制的に同期させます。`clk`のすべての登録された時間をそれに応じて変更します。`clk.unit`を`to.unit`に変換または強制します。
