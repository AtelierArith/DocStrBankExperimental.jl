estimate_parameters

`x_min` と `α` を、[コルモゴロフ-スミルノフ検定](https://www.encyclopediaofmath.org/index.php/Kolmogorov-Smirnov_test)に関して与えられたデータセットに対して推定します。

# パラメータ

  * `data::AbstractArray`: 分布にフィットさせるべきデータの配列。
  * `distribution::Type`: 分布のタイプ、すなわち `ContinuousPowerLaw` または `DiscretePowerLaw`。
  * `xmins::AbstractArray`: 指定されていない場合、`data` のすべてのユニークな値が可能な `x_min` として取られます。指定されている場合、最良の `x_min` を見つける際には `xmins` の値のみが考慮されます。
  * `xmax::Int64`: 計算において考慮される最大値。例えば、コルモゴロフ-スミルノフ検定を計算する際には、`xmax` を超える値は考慮されません。

# 戻り値

  * `best_fit::distribution`: 与えられたパラメータにフィットした `distribution` タイプの分布。
  * `KS::Float64`: データとフィットした分布との間のコルモゴロフ-スミルノフ距離。
