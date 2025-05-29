```
fit(LassoPath, X, y, d=Normal(), l=canonicallink(d); ...)
```

は、設計行列 `X` と応答 `y` に基づいて線形または一般化線形のLassoパスをフィットします：

$$
\underset{\beta,b_0}{\operatorname{argmin}} -\frac{1}{N} \mathcal{L}(y|X,\beta,b_0) + \lambda\left[(1-\alpha)\frac{1}{2}\|\beta\|_2^2 + \alpha\|\beta\|_1\right]
$$

ここで、$0 \le \alpha \le 1$ はリッジ回帰（$\alpha = 0$）とLasso回帰（$\alpha = 1$）のバランスを設定し、$N$ は $X$ の行数です。オプションの引数 `d` は応答の条件付き分布を指定し、`l` はリンク関数を指定します。Lasso.jl は、GLM.jl からサポートされている分布とリンク関数を継承します。デフォルトは線形Lassoパスをフィットすることであり、すなわち `d=Normal(), l=IdentityLink()`、または $\mathcal{L}(y|X,\beta) = -\frac{1}{2}\|y - X\beta - b_0\|_2^2 + C$ です。

# 例

```julia
fit(LassoPath, X, y)    # L1正則化線形回帰
fit(LassoPath, X, y, Binomial(), Logit();
    α=0.5) # エラスティックネットの組み合わせによる二項ロジット回帰
           # 0.5 L1 と 0.5 L2 の正則化ペナルティ
```

# 引数

  * `wts=ones(length(y))`: 各観測値の重み
  * `offset=zeros(length(y))`: 各観測値のオフセット
  * `λ`: モデルがフィットされる特定のλ値のセットを指定するために使用できます。   `λ` の明示的な値の `AbstractVector` を渡すか、   そのような値を返す関数 `λfunc(λmax)` を渡すことができます。ここで、`λmax` は null モデルを生成する最小の `λ` 値です。   `λ` が指定されていない場合、Lasso.jl は `λmax` から `λminratio * λmax` までの `nλ` の対数的に間隔を空けた `λ` 値を選択します。
  * `α=1`: リッジ回帰（$\alpha = 0$）とLasso回帰（$\alpha = 1$）のバランスを制御する0から1の間の値。   `λ` が指定されていない場合、`α` は0に設定できませんが、1には設定できます。
  * `nλ=100` 使用する `λ` 値の数
  * `λminratio=1e-4` 予測子よりも観測値が多い場合、そうでなければ0.001。
  * `stopearly=true`: `true` の場合、説明された逸脱の割合が   0.999を超えるか、連続するλ値によって説明された逸脱の差が `1e-5` を下回ると、パスが早期に停止します。
  * `standardize=true`: フィッティングの前に予測子を単位標準偏差に標準化するかどうか。
  * `intercept=true`: （ペナルティなしの）モデルの切片 $b_0$ をフィットするかどうか。false の場合、$b_0=0$ になります。
  * `algorithm`: 使用するアルゴリズム。   `NaiveCoordinateDescent` は、残差との予測子の内積を反復的に計算しますが、   `CovarianceCoordinateDescent` アルゴリズムは、事前に計算されたグラム行列を使用します。   `NaiveCoordinateDescent` は、モデルに入らない多くの予測子がある場合や、   一般化線形モデルをフィッティングする場合に通常は速くなります。   デフォルトでは、観測値の5倍以上の予測子がある場合やモデルがGLMの場合は `NaiveCoordinateDescent` を使用します。それ以外は `CovarianceCoordinateDescent` です。
  * `randomize=true`: 座標降下法によって係数が更新される順序をランダム化するかどうか。これは、係数が高い相関を持つ場合に収束を大幅に加速できます。
  * `rng=RNG_DEFAULT`: 係数の反復に使用される乱数生成器。
  * `maxncoef=min(size(X, 2), 2*size(X, 1))`: モデルに許可される最大係数の数。これを超えるとエラーが発生します。
  * `dofit=true`: 構築時にモデルをフィットするかどうか。`false` の場合、   後で `fit!(model)` を呼び出すことでモデルをフィットできます。
  * `cd_maxiter=100_000`: 座標降下法の最大反復回数。
  * `cd_tol=1e-7`: 内部ループの座標降下法の反復に対する許容誤差。
  * `irls_maxiter=30`: 反復的に重み付けされた最小二乗ループの最大反復回数。これは、モデルが一般化線形モデルでない限り無視されます。
  * `irls_tol=1e-7`: 外部の反復的に重み付けされた最小二乗反復に対する許容誤差。これは、モデルが一般化線形モデルでない限り無視されます。
  * `criterion=:coef` 収束基準。`cd_tol` と `irls_tol` の解釈方法を制御します。可能な値は：

      * `:coef`: モデルは、連続する反復間の係数の最大絶対二乗差が指定された許容誤差を下回ると収束したと見なされます。これは glmnet によって使用される基準です。
      * `:obj`: モデルは、連続する反復間のLasso/Elastic Net目的の相対変化が指定された許容誤差を下回ると収束したと見なされます。これは GLM.jl によって使用される基準です。
  * `minStepFac=0.001`: バックトラッキングラインサーチの最小ステップ割合。
  * `penalty_factor=ones(size(X, 2))`: 各係数 $j$ に対する別々のペナルティファクター $\omega_j$、すなわち $\lambda$ の代わりにペナルティは   $\lambda\omega_j$ になります。   ペナルティファクターは内部的に変数の数に合計されるように再スケーリングされます（`glmnet.R` の慣例）。
  * `standardizeω=true`: ペナルティファクターを変数の数に合計するようにスケーリングするかどうか（glmnet.R の慣例）。

```
