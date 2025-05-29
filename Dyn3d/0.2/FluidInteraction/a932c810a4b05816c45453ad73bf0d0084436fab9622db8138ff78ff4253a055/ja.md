```
AcquireBodyGridKinematics(bd::BodyDyn, bgs::Vector{BodyGrid})
```

更新された bd 構造体が与えられ、各ボディの 3d bs[i].x*i が慣性フレーム内にあり、6d bs[i].v がボディローカルフレーム内にある場合、慣性フレーム内の各ボディポイントの 3d 線形 q*i と v_i を返します。
