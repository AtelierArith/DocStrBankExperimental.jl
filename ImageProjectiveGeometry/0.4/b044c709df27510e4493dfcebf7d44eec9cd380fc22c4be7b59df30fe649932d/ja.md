invrpy - ロールピッチヨー変換の逆

```
使用法:  (rpy1, rpy2) = invrpy(RPY)
 
引数:  RPY - 4x4 同次変換行列または 3x3 回転行列

戻り値:  rpy1 = [phi1, theta1, psi1] - 1つ目の解と
          rpy2 = [phi2, theta2, psi2] - 2つ目の解

   rotz(phi1)  * roty(theta1)  * rotx(psi1)    = RPY
 rotz(rpy1[1]) * roty(rpy1[2]) * rotx(rpy1[3]) = RPY
```

参照: inveuler(), invht(), rotx(), roty(), rotz()
