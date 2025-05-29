```
@bitmask [exported = false] BitFlags::UInt32 begin
    FLAG_A = 1
    FLAG_B = 2
    FLAG_C = 2^2 # == 4 (if you didn't know)
    FLAG_AB = FLAG_A | FLAG_B
end

@bitmask [exported = false] BitFlags::UInt32 begin
    FLAG_A = 1
    FLAG_B # unspecified, will have the mask after 0x01, i.e. 0x02.
    FLAG_C = 4
    FLAG_AB = FLAG_A | FLAG_B
end
```

Enumeration of bitmask flags that can be combined with `&`, `|` and `xor`, forbidding the combination of flags from different BitMasks.

If `exported` is set to true with a first argument of the form `exported = <false|true>`, then all the values and the defined type will be exported.

If a flag is left unspecified, it will inherit the value after the previous declaration that is not a combination of other flags.

!!! warn
    If there are any unspecified flags, all non-combination values should be declared in an ascending order to guarantee that the flags generated automatically will not alias another one.

