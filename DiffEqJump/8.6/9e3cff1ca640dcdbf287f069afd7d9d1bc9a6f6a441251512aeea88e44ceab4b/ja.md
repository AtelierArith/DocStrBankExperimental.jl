Gillespieの直接法。`ConstantRateJump`のレートと影響は`FunctionWrappers`を介して保存されており、これは非常に多くの`ConstantRateJump`に対して`Direct`よりもパフォーマンスが向上します。しかし、そのような多くのジャンプに対しては、通常、異なるクラスのアグリゲーター（すなわち、`SortingDirect`、`DirectCR`、`RSSA`または`RSSACR`）の方がはるかにパフォーマンスが良いです。

Gillespie, Daniel T. (1976). A General Method for Numerically Simulating the Stochastic Time Evolution of Coupled Chemical Reactions. Journal of Computational Physics. 22 (4): 403–434. doi:10.1016/0021-9991(76)90041-3.
