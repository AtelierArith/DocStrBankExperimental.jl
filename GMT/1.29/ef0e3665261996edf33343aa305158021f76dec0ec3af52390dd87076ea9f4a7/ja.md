```
xc, yc, R, err = circfit(x,y; taubin=false)
```

x,y平面に円をフィットさせます。

FEXの寄稿から https://www.mathworks.com/matlabcentral/fileexchange/5557-circle-fit

### 引数

  * `xy`: n点のx,y座標を持つMx2行列またはGMTdataset
  * `x,y`: 代わりに、各(x(i),y(i))が与えられた点である2つのベクトルを渡します

### オプション

  * `taubin`: $true$の場合、代わりにTaubinアルゴリズムを使用します。 https://people.cas.uab.edu/~mosya/cl/TaubinSVD.m はこれを最良のアルゴリズムとして推奨しています。デフォルトの方法より約2倍遅いです。

### 戻り値

  * `xc`, `yc`, `R`, `err`; フィットの中心、半径、および誤差
