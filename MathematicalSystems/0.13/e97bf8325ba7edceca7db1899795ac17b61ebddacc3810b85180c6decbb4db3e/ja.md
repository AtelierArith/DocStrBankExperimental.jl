```
discretize(system::AbstractContinuousSystem, ΔT::Real,
           algorithm::AbstractDiscretizationAlgorithm=ExactDiscretization(),
           constructor=_default_complementary_constructor(system))
```

`isaffine` `AbstractContinuousSystem`の離散化を、離散化手法`algorithm`を用いてサンプリング時間`ΔT`で`AbstractDiscreteSystem`に変換します。

### 入力

  * `system`      – アフィン連続システム
  * `ΔT`          – サンプリング時間
  * `algorithm`   – （オプション、デフォルト: `ExactDiscretization()`）離散化アルゴリズム
  * `constructor` – （オプション、デフォルト: `_default_complementary_constructor(system)`）構築方法

### 出力

入力システム`system`の離散化を、離散化手法`algorithm`とサンプリング時間`ΔT`を用いて返します。
