```
gauss3(cx, cy, cz, wx, wy, wz, Φ=0, Θ=0, value::Number = 1)
gauss3(center::NTuple{3,RealU}, radii::NTuple{3,RealU}=(1,1,1), angle::NTuple{2,RealU}=(0,0), v=1)
gauss3(r, v=1) (幅 `w` の等方性)

パラメータから `Object{Gauss3}` を構築します; ここで `width` = FWHM (半最大幅) です。
```
