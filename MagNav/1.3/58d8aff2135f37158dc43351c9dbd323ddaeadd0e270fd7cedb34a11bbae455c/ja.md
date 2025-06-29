```
get_pinson(nx::Int, lat, vn, ve, vd, fn, fe, fd, Cnb;
           baro_tau         = 3600.0,
           acc_tau          = 3600.0,
           gyro_tau         = 3600.0,
           fogm_tau         = 600.0,
           vec_states::Bool = false,
           fogm_state::Bool = true,
           k1=3e-2, k2=3e-4, k3=1e-6)
```

`nx` x `nx` ピンソンダイナミクスマトリックスを取得します。状態（誤差）は次のとおりです：

| **Num** | **State** | **Units** | **Description** |
|:------- |:--------- |:--------- |:--------------- |
| 1       | lat       | rad       | 緯度              |
| 2       | lon       | rad       | 経度              |
| 3       | alt       | m         | 高度              |
| 4       | vn        | m/s       | 北方向の速度          |
| 5       | ve        | m/s       | 東方向の速度          |
| 6       | vd        | m/s       | 下方向の速度          |
| 7       | tn        | rad       | 北方向の傾き（姿勢）      |
| 8       | te        | rad       | 東方向の傾き（姿勢）      |
| 9       | td        | rad       | 下方向の傾き（姿勢）      |
| 10      | ha        | m         | バロメーター補正高度      |
| 11      | a_hat     | m/s^2     | バロメーター補正垂直加速度   |
| 12      | ax        | m/s^2     | x加速度計           |
| 13      | ay        | m/s^2     | y加速度計           |
| 14      | az        | m/s^2     | z加速度計           |
| 15      | gx        | rad/s     | xジャイロスコープ       |
| 16      | gy        | rad/s     | yジャイロスコープ       |
| 17      | gz        | rad/s     | zジャイロスコープ       |
| end     | S         | nT        | FOGMキャッチオール     |

**引数:**

  * `nx`:         総状態次元
  * `lat`:        緯度       [rad]
  * `vn`:         北方向の速度 [m/s]
  * `ve`:         東方向の速度 [m/s]
  * `vd`:         下方向の速度 [m/s]
  * `fn`:         北方向の特定の力 [m/s^2]
  * `fe`:         東方向の特定の力 [m/s^2]
  * `fd`:         下方向の特定の力 [m/s^2]
  * `Cnb`:        方向余弦行列（ボディからナビゲーション） [-]
  * `baro_tau`:   （オプション）バロメーターの時間定数 [s]
  * `acc_tau`:    （オプション）加速度計の時間定数 [s]
  * `gyro_tau`:   （オプション）ジャイロスコープの時間定数 [s]
  * `fogm_tau`:   （オプション）FOGMキャッチオールの時間定数 [s]
  * `vec_states`: （オプション）trueの場合、ベクトル磁力計の状態を含める
  * `fogm_state`: （オプション）trueの場合、FOGMキャッチオールのバイアス状態を含める
  * `k1`:         （オプション）バロメーター補正定数 [1/s]
  * `k2`:         （オプション）バロメーター補正定数 [1/s^2]
  * `k3`:         （オプション）バロメーター補正定数 [1/s^3]

**戻り値:**

  * `F`: `nx` x `nx` ピンソンマトリックス

```
