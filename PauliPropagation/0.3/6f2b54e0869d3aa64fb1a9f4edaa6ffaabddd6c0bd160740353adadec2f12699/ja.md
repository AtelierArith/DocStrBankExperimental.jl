```
applyandadd!(gate::CliffordGate, pstr, coeff, theta, output_psum; kwargs...)
```

`CliffordGate`ゲートのための`applyandadd!`のオーバーロード。Cliffordゲートは重ならないパウリ文字列を生成するため、`add!()`の代わりに`set!()`を使用します。`applytoall!`は適応する必要はありません。
