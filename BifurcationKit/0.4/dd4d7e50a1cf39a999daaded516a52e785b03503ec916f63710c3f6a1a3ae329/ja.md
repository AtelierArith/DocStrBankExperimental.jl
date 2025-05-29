```julia
predictor(
    bp,
    δp;
    verbose,
    ampfactor,
    nbfailures,
    maxiter,
    perturb,
    J,
    normN,
    optn
)

```

この関数は、パラメータ値 `δp` に対して、縮小方程式 / 正規形のゼロがどのようになるべきかを予測します。これらのゼロを見つけるためのアルゴリズムは、縮小ニュートンに基づいています。

## オプション引数

  * `J` 正規形のヤコビ行列。ForwardDiff で評価されます。
  * `perturb` 縮小ニュートンで使用される摂動関数
  * `normN` ニュートンに使用されるノルム。
