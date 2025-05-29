```
I = togglemask(I::Union{GMTimage{<:Bool, 2}, GMTimage{<:UInt8, 2}}) -> GMTimage
```

マスク画像のUInt8とブール表現の間で変換します。入力データのコピーを持つ新しいオブジェクトが返されます。
