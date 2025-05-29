```
ModifiedKey
```

修飾子を持つキー。`|`を使って便利に構築できます。例えば、Ctrl+Aの場合は`ctrl | CharKey('a')`です。すべての組み合わせが使用できるわけではないことに注意してください。例えば、Ctrl+JとCtrl+Mはどちらも[RETURN]と同じです。

`|`を使って組み合わせることは、ほぼ常により読みやすくなります。例えば、`ModKey(0x03, CharKey('q')`の代わりに`alt | ctrl | CharKey('q')`を使用します。

# フィールド

mod_bitmap::UInt8 - 修飾キーのビットマップ; LSBから: Alt, Ctrl, Shiftキー::Union{CharKey, SpecialKey} - 基本キー
