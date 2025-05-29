```
newton = NewtonFlash()
newton = NewtonFlash(dMax = 0.2)
```

ゼロ解のためのニュートン法を使用したフラッシュ。条件付き収束のみですが、SSIよりも収束率が良いです。

# 引数

  * `dMax`: ニュートン反復のための減衰係数

関連情報: [`flash_2ph!`](@ref), [`SSIFlash`](@ref) [`SSINewtonFlash`](@ref)
