```
@bitmask [exported = false] BitFlags::UInt32 begin
    FLAG_A = 1
    FLAG_B = 2
    FLAG_C = 2^2 # == 4 (もし知らなかったら)
    FLAG_AB = FLAG_A | FLAG_B
end

@bitmask [exported = false] BitFlags::UInt32 begin
    FLAG_A = 1
    FLAG_B # 未指定、0x01の後のマスクを持つ、すなわち0x02。
    FLAG_C = 4
    FLAG_AB = FLAG_A | FLAG_B
end
```

`&`、`|`、および `xor` で組み合わせることができるビットマスクフラグの列挙。異なる BitMask からのフラグの組み合わせは禁止されています。

`exported` が `exported = <false|true>` の形式の最初の引数で true に設定されている場合、すべての値と定義された型がエクスポートされます。

フラグが未指定の場合、他のフラグの組み合わせではない前の宣言の後の値を継承します。

!!! warn
    未指定のフラグがある場合、すべての非組み合わせ値は昇順で宣言されるべきであり、自動的に生成されるフラグが他のフラグとエイリアスしないことを保証します。

