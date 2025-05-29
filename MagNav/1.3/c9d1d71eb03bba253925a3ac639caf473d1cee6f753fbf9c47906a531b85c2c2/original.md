```
nekf_train(lat, lon, alt, vn, ve, vd, fn, fe, fd, Cnb, meas, dt,
           itp_mapS, x_nn::Matrix, y_nn::Matrix;
           P0                   = create_P0(),
           Qd                   = create_Qd(),
           R                    = 1.0,
           baro_tau             = 3600.0,
           acc_tau              = 3600.0,
           gyro_tau             = 3600.0,
           fogm_tau             = 600.0,
           η_adam               = 0.1,
           epoch_adam::Int      = 10,
           hidden::Int          = 1,
           activation::Function = swish,
           l_window::Int        = 50,
           date                 = get_years(2020,185),
           core::Bool           = false)
```

Train a measurement noise covariance-adaptive neural extended Kalman filter (nEKF) model for airborne magnetic anomaly navigation.

**Arguments:**

  * `lat`:        latitude  [rad]
  * `lon`:        longitude [rad]
  * `alt`:        altitude  [m]
  * `vn`:         north velocity [m/s]
  * `ve`:         east  velocity [m/s]
  * `vd`:         down  velocity [m/s]
  * `fn`:         north specific force [m/s^2]
  * `fe`:         east  specific force [m/s^2]
  * `fd`:         down  specific force [m/s^2]
  * `Cnb`:        direction cosine matrix (body to navigation) [-]
  * `meas`:       scalar magnetometer measurement [nT]
  * `dt`:         measurement time step [s]
  * `itp_mapS`:   scalar map interpolation function (`f(lat,lon)` or `f(lat,lon,alt)`)
  * `x_nn`:       `N` x `Nf` data matrix for neural network (`Nf` is number of features)
  * `y_nn`:       `y` target matrix for neural network (`[latitude longitude]`)
  * `P0`:         (optional) initial covariance matrix
  * `Qd`:         (optional) discrete time process/system noise matrix
  * `R`:          (optional) measurement (white) noise variance
  * `baro_tau`:   (optional) barometer time constant [s]
  * `acc_tau`:    (optional) accelerometer time constant [s]
  * `gyro_tau`:   (optional) gyroscope time constant [s]
  * `fogm_tau`:   (optional) FOGM catch-all time constant [s]
  * `η_adam`:     (optional) learning rate for Adam optimizer
  * `epoch_adam`: (optional) number of epochs for Adam optimizer
  * `hidden`:     (optional) hidden layers & nodes (e.g., `[8,8]` for 2 hidden layers, 8 nodes each)
  * `activation`: (optional) activation function

      * `relu`  = rectified linear unit
      * `σ`     = sigmoid (logistic function)
      * `swish` = self-gated
      * `tanh`  = hyperbolic tan
      * run `plot_activation()` for a visual
  * `l_window`:   (optional) temporal window length
  * `date`:       (optional) measurement date (decimal year) for IGRF [yr]
  * `core`:       (optional) if true, include core magnetic field in measurement

**Returns:**

  * `m`: neural network model
