中間CG状態変数は、`cg`および`cg!`内で使用されます。`u`、`r`、および`c`は、`cg`または`cg!`の解と同じ型である必要があります。

```
struct CGStateVariables{T,Tx<:AbstractArray{T}}
    u::Tx
    r::Tx
    c::Tx
end
```
