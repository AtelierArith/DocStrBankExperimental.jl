decomposecamera - カメラ投影行列の分解

```
Usage:  K, Rc_w, Pc, pp, pv = decomposecamera(P)

   P は P = K*(R -R*Pc) の形に分解されます。

Argument:  P - 3 x 4 カメラ投影行列
Returns:
           K - 次の形のキャリブレーション行列
                 |  ax   s   ppx |
                 |   0   ay  ppy |
                 |   0   0    1  |

               ここで:
               ax = f/pixel_width および ay = f/pixel_height,
               ppx および ppy はピクセル単位の主点を定義し、
               s はカメラスキューです。
        Rc_w - カメラフレームに対する世界座標系を定義する 3 x 3 回転行列
               R の列の転置は、世界座標系におけるカメラの X, Y, Z 軸の方向を定義します。
          Pc - 世界座標系におけるカメラ中心位置。
          pp - 画像の主点。
          pv - カメラ中心 C から pp を通って外向きに指す主ベクトル。
               これは主点が画像の中心にない場合、R'(:,3) と同じではないかもしれませんが、類似しているはずです。
```

See also: rq3()
