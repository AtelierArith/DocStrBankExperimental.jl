```
mellanize(imagefile, side=500;
    lineweight       =  5.0, # ピクセルの灰色値 [0,1] を掛けてこの線の幅を得る
    minlineweight    =  0.0,
    foregroundcolor  =  "black",
    backgroundcolor  =  "antiquewhite2",
    startradius      =  5.0,   # 開始半径
    margin           =  5,
    tightness         = 2.0,  # 各ステップで半径がどれだけ伸びるかを制御
    chord            =  2.0, # 各ストロークの長さ
    annotation       =  false,
    output           =  ""
    )
```

where `imagefile` is path of 8bit PNG or JPG, and `side` is the required image size.
