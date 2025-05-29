```
@unitdim(U::UnitSystem,F,M,L,T,Q,Θ,N,J="lm",A="rad")
```

`U::UnitSystem`の各基底次元の`print`出力を、`String`入力引数`force`、`mass`、`length`、`time`、`charge`、`temperature`、`molaramount`、`luminousflux`、`angle`に対して指定します。

```Julia
@unitdim Gauss "gf" "g" "cm" "s" "C" "K" "mol"
@unitdim Metric "kgf" "kg" "m" "s" "C" "K" "mol"
@unitdim British "lb" "slug" "ft" "s" "C" "°R" "slug-mol"
@unitdim IPS "lb" "slinch" "in" "s" "C" "°R" "slinch-mol"
@unitdim FPS "pdl" "lb" "ft" "s" "C" "°R" "lb-mol"
@unitdim English "lbf" "lbm" "ft" "s" "C" "°R" "lb-mol"
@unitdim IAU☉ "M☉f" "M☉" "au" "D" "C" "K" "mol"
```

これらの標準例は、いくつかの組み込みデフォルトです。
