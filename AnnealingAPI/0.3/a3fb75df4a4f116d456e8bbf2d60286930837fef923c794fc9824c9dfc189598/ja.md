```
update_corrfns!(tracker, value, index)
```

この関数は、`tracker[index] = value`を書くのと同等ですが、`rollback!`を呼び出すことでトラッカーを前の状態に迅速に戻すことができるロールバックハンドルも返します。

関連情報: [`rollback!`](@ref).
