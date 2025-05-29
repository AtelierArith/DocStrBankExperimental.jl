```
fit(RegularizedModel, X, y, dist, link; <kwargs>)
```

選択された正則化パスのセグメントを表すLinearModelまたはGeneralizedLinearModelを返します。

# 例

```julia
fit(LassoModel, X, y; select=MinBIC()) # BICを最小化するLinearModel
fit(LassoModel, X, y, Binomial(), Logit();
    select=MinCVmse(path, 5)) # 5分割CV mseを最小化するモデル
```

# 引数

  * `select::SegSelect=MinAICc()`: セグメントセレクタ。
  * `wts=ones(length(y))`: 各観測値の重み
  * `offset=zeros(length(y))`: 各観測値のオフセット
  * `λ`: モデルがフィットされる特定のλ値のセットを指定するために使用できます。λが指定されていない場合、Lasso.jlは`λmax`から`λminratio * λmax`までのnλ対数間隔のλ値を選択します。`λmax`は、nullモデルを生成する最小のλ値です。
  * `nλ=100` 使用するλ値の数
  * `λminratio=1e-4` 予測子よりも観測値が多い場合はそれ以外は0.001。
  * `stopearly=true`: `true`の場合、説明された逸脱の割合が0.999を超えるか、連続するλ値によって説明された逸脱の差が`1e-5`を下回ると、パスは早期に停止します。
  * `standardize=true`: フィッティングの前に予測子を単位標準偏差に標準化するかどうか。
  * `intercept=true`: (ペナルティなしの)モデルの切片をフィットするかどうか。
  * `algorithm`: 使用するアルゴリズム。`NaiveCoordinateDescent`は、残差との予測子の内積を反復的に計算します。これに対して、`CovarianceCoordinateDescent`アルゴリズムは、事前に計算されたグラム行列を使用します。`NaiveCoordinateDescent`は、モデルに入らない多くの予測子がある場合や、一般化線形モデルをフィットする場合に通常は速くなります。デフォルトでは、観測値の5倍以上の予測子がある場合やモデルがGLMの場合は`NaiveCoordinateDescent`を使用します。それ以外は`CovarianceCoordinateDescent`。
  * `randomize=true`: 座標降下法によって係数が更新される順序をランダム化するかどうか。係数が高く相関している場合、収束を大幅に加速できます。
  * `maxncoef=min(size(X, 2), 2*size(X, 1))`: モデルに許可される最大係数の数。これを超えるとエラーが発生します。
  * `dofit=true`: 構築時にモデルをフィットするかどうか。`false`の場合、`fit!(model)`を呼び出すことで後でモデルをフィットできます。
  * `cd_tol=1e-7`: 内部ループでの座標降下法の反復の許容誤差。
  * `irls_tol=1e-7`: 外部の反復加重最小二乗法の反復の許容誤差。モデルが一般化線形モデルでない限り、これは無視されます。
  * `criterion=:coef` 収束基準。`cd_tol`と`irls_tol`の解釈方法を制御します。可能な値は：

      * `:coef`: モデルは、連続する反復間の係数の最大絶対二乗差が指定された許容誤差を下回ると収束したと見なされます。これはglmnetで使用される基準です。
      * `:obj`: モデルは、連続する反復間のLasso/Elastic Net目的の相対変化が指定された許容誤差を下回ると収束したと見なされます。これはGLM.jlで使用される基準です。
  * `minStepFac=0.001`: バックトラッキングラインサーチの最小ステップ割合。
  * `penalty_factor=ones(size(X, 2))`: 各係数$j$に対する別々のペナルティファクター$\omega_j$、すなわち$\lambda$の代わりにペナルティは$\lambda\omega_j$になります。ペナルティファクターは内部的に変数の数に合計されるように再スケーリングされます（`glmnet.R`の慣例）。
  * `standardizeω=true`: ペナルティファクターを変数の数に合計するようにスケーリングするかどうか（glmnet.Rの慣例）。

引数のより完全なリストについては、[`fit(::Type{LassoPath}, ::Matrix{Float64}, ::Vector{Float64})`](@ref)も参照してください。
