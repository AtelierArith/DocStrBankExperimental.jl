```
generic(i)
```

汎用インターバルを返します。すなわち、オクターブの剰余での音階のステップ数です。[`degree`](@ref)とは異なり、結果はインターバルの符号を尊重します（ユニゾン=`0`、上の2度=`1`、下の2度=`-1`）。音高については、[`degree`](@ref)を使用してください。

参照: [`degree`](@ref), [`diasteps`](@ref)
