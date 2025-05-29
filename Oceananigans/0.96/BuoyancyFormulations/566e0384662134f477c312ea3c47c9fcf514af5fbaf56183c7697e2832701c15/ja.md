```
LinearEquationOfState([FT=Float64;] thermal_expansion=1.67e-4, haline_contraction=7.80e-4)
```

`SeawaterBuoyancy`のための`LinearEquationOfState`を返します。`thermal_expansion`係数と`haline_contraction`係数を使用します。`LinearEquationOfState`の浮力摂動$b$は次のようになります。

$$
    b = g (α T - β S),
$$

ここで、$g$は重力加速度、$α$は`thermal_expansion`、$β$は`haline_contraction`、$T$は温度、$S$は実用塩分単位です。

`thermal_expansion`と`haline_contraction`のデフォルト定数は、Vallisの「Atmospheric and Oceanic Fluid Dynamics: Fundamentals and Large-Scale Circulation」（第2版、2017年）の表1.2（33ページ）から取られています。
