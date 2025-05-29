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

Get the `nx` x `nx` Pinson dynamics matrix. States (errors) are:

| **Num** | **State** | **Units** | **Description**                        |
|:------- |:--------- |:--------- |:-------------------------------------- |
| 1       | lat       | rad       | latitude                               |
| 2       | lon       | rad       | longitude                              |
| 3       | alt       | m         | altitude                               |
| 4       | vn        | m/s       | north velocity                         |
| 5       | ve        | m/s       | east  velocity                         |
| 6       | vd        | m/s       | down  velocity                         |
| 7       | tn        | rad       | north tilt (attitude)                  |
| 8       | te        | rad       | east  tilt (attitude)                  |
| 9       | td        | rad       | down  tilt (attitude)                  |
| 10      | ha        | m         | barometer aiding altitude              |
| 11      | a_hat     | m/s^2     | barometer aiding vertical acceleration |
| 12      | ax        | m/s^2     | x accelerometer                        |
| 13      | ay        | m/s^2     | y accelerometer                        |
| 14      | az        | m/s^2     | z accelerometer                        |
| 15      | gx        | rad/s     | x gyroscope                            |
| 16      | gy        | rad/s     | y gyroscope                            |
| 17      | gz        | rad/s     | z gyroscope                            |
| end     | S         | nT        | FOGM catch-all                         |

**Arguments:**

  * `nx`:         total state dimension
  * `lat`:        latitude       [rad]
  * `vn`:         north velocity [m/s]
  * `ve`:         east  velocity [m/s]
  * `vd`:         down  velocity [m/s]
  * `fn`:         north specific force [m/s^2]
  * `fe`:         east  specific force [m/s^2]
  * `fd`:         down  specific force [m/s^2]
  * `Cnb`:        direction cosine matrix (body to navigation) [-]
  * `baro_tau`:   (optional) barometer      time constant [s]
  * `acc_tau`:    (optional) accelerometer  time constant [s]
  * `gyro_tau`:   (optional) gyroscope      time constant [s]
  * `fogm_tau`:   (optional) FOGM catch-all time constant [s]
  * `vec_states`: (optional) if true, include vector magnetometer states
  * `fogm_state`: (optional) if true, include FOGM catch-all bias state
  * `k1`:         (optional) barometer aiding constant [1/s]
  * `k2`:         (optional) barometer aiding constant [1/s^2]
  * `k3`:         (optional) barometer aiding constant [1/s^3]

**Returns:**

  * `F`: `nx` x `nx` Pinson matrix
