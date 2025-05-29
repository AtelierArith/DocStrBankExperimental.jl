```
    bacon(setting, m, method, alpha)
```

回帰データの外れ値を検出するためにBACONアルゴリズムを実行します。

# 引数:

  * `setting`: フォーミュラとデータセットを持つRegressionSettingオブジェクト。
  * `m`: 初期サブセットに含める要素の数。
  * `method`: 初期サブセットのポイントを選択するために使用する距離法。
  * `alpha`: カットオフに使用される分位数。

# 説明

BACON（Blocked Adaptive Computationally efficient Outlier Nominators）アルゴリズムは、以下の引用で定義されており、さまざまなバージョンがあります。たとえば、BACONは多変量データ用、回帰用などです。回帰モデルの設計行列は多変量データであるため、BACONはアルゴリズムの初期段階で多変量データ用に実行されます。クリーンな観測値のサブセットを選択した後、前方探索が適用されます。高い標準化残差を持つ観測値は外れ値として報告されます。

# 出力

  * `["outliers"]`: 外れ値のインデックスの配列。
  * `["betas"]`: 推定された係数の配列。

# 例

```julia-repl
julia> reg = createRegressionSetting(@formula(stackloss ~ airflow + watertemp + acidcond), stackloss)
julia> bacon(reg, m=12)
Dict{String, Vector} with 2 entries:
  "betas"    => [-37.6525, 0.797686, 0.57734, -0.0670602]
  "outliers" => [1, 3, 4, 21]
```

# 参考文献

Billor, Nedret, Ali S. Hadi, and Paul F. Velleman. "BACON: blocked adaptive computationally efficient outlier nominators." Computational statistics & data analysis 34.3 (2000): 279-298.
