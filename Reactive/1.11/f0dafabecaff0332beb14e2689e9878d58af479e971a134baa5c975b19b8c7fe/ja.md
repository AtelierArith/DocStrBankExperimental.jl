```
`bind!(dest, src, twoway=true; initial=true)`
```

`src`のすべての更新に対して、`dest`も同じ値で更新され、`twoway`がtrueの場合はその逆も行われます。`initial`がfalseの場合、`dest`は`src`が次に更新されるときにのみ`src`の値に更新されます。それ以外の場合（`initial`がtrueの場合）、`dest`と`src`は即座に`src`の値を取ります。
