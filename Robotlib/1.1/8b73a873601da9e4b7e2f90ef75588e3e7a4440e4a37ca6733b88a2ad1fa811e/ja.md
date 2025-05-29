```
Rf, m = calib_force(POSES, F, m0::Real = 0.3; offset=true)
Rf, m = calib_force(POSES, F, g::Vector; offset=true)
```

`POSES` ∈ ℜ(4,4,N) はロボットの前方運動学からのツールフレームの位置であり、4x4の変換行列 `F` ∈ ℜ(N,3) は力のベクトル（トルクを含む ℜ(Nx6) 行列も受け入れます）

# 使用法

```
Rf*force[i,1:3] + forceoffs = POSES[1:3,1:3,i]'*[0, 0, mf*-9.82]
```

`m0` が提供されると、重力ベクトルは [0,0,-g] であると仮定され、言い換えれば、重力は負の z 軸に沿って作用していると考えられます。カスタム重力ベクトル `g` も提供できます。

この関数は加速度計のキャリブレーションにも使用できます。

[Bagge Carlson, F.](https://www.control.lth.se/staff/fredrik-bagge-carlson/)、["Machine Learning and System Identification for Estimation in Physical Systems"](https://lup.lub.lu.se/search/publication/ffb8dc85-ce12-4f75-8f2b-0881e492f6c0) (博士論文 2018)。

`calib_force_iterative` および `calib_force_eigen` も参照してください。
