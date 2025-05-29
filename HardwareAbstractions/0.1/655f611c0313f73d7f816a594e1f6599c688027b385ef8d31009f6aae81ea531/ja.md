```
@periodically(h, simulation::Bool, body)
```

`h >= 0.001`秒の間隔でbodyが実行されることを保証します。`simulation == false`の場合、スリープは行われません。
