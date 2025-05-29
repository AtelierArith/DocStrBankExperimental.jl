```
is_two_qubit(g::Gate; stim_supported::Bool = false)
```

ゲート `g` がサポートされている2量子ビットゲートであれば `true` を返し、そうでなければ `false` を返します。`stim_supported` が `true` の場合、Stim によってもサポートされているゲートに制限されます。
