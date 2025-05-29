```
`bindmap!(dest::Signal, src2dest::Function, src::Signal, dest2src=nothing; initial=true)`
```

`src`のすべての更新に対して、`dest`を修正された値（関数`src2dest`を使用）で更新し、`dest2src`が指定されている場合は双方向の更新が保持されます。`initial`がfalseの場合、`dest`は`src`が次に更新されるときにのみ`src`の修正された値に更新されます。それ以外の場合（`initial`がtrueの場合）、`dest`と`src`はそれぞれの修正された値を即座に取得します。
