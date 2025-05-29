```
exactconv(I, x::F) :: Union{I,Nothing}
exactconv(F, x::I) :: Union{F,Nothing}
```

整数型と浮動小数点型の間で変換します。変換は数値の値が変わらない場合にのみ成功し、そうでない場合は `nothing` を返します。
