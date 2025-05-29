```
flux_godunov(u_ll, u_rr, orientation_or_normal_direction, 
             equations::LinearScalarAdvectionEquation2D)
```

2D線形スカラー輸送方程式のためのゴドノフ（アップウィンド）フラックス。基本的には一次のアップウィンドです。詳細は、例えば https://math.stackexchange.com/a/4355076/805029 を参照してください。
