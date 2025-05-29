```
SIAMFANLEquationsJL(;
    method = :newton, delta = 1e-3, linsolve = nothing, autodiff = missing
)
```

### キーワード引数

  * `method`: 非線形システムを解くための手法の選択。
  * `delta`: 初期擬似時間ステップ、デフォルトは1e-3。
  * `linsolve` : JFNK線形ソルバー、選択肢は`gmres`と`bicgstab`。
  * `m`: アンダーソン加速の深さ、デフォルトはピカード反復のために0。
  * `beta`: アンダーソン混合パラメータ、f(x)を(1-beta)x+beta*f(x)に変更し、減衰ピカード反復を加速するのと同等。
  * `autodiff`: デフォルトは`missing`、これは`f.jac`が提供されていない場合に`SIAMFANLEquations`がヤコビ行列を構築することを意味します。他の場合には、他のNonlinearSolveソルバーと同様のヤコビ行列を生成するために使用します。

### サブメソッドの選択

  * `:newton`: 古典的なニュートン法。
  * `:pseudotransient`: 擬似過渡法。
  * `:secant`: スカラー方程式のためのセカント法。
  * `:anderson`: 固定点反復のためのアンダーソン加速。

!!! 注     このアルゴリズムは`SIAMFANLEquations.jl`がインストールされ、ロードされている場合にのみ利用可能です。
