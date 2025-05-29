```
NFQ{A<:AbstractApproximator, F, R} <: AbstractLearner
NFQ(action_space::AbstractVector, approximator::A, num_iterations::Integer, epochs::Integer, loss_function::F, rng::R, γ::Float32) where {A, F, R}
```

Neural Fitted Q-iteration as implemented in [1]

# キーワード引数

  * `action_space::AbstractVector` 環境のアクション空間（optimize!ステップで必要）
  * `approximator::A` Q関数近似器（通常はニューラルネットワーク）
  * `num_iterations::Integer` FQIループ内の価値反復の反復回数（すなわち外側のループ）
  * `epochs::Integer` 各反復でニューラルネットワークを訓練するエポック数
  * `loss_function::F` NNの損失関数
  * `rng::R` 擬似乱数生成器
  * `γ::Float32` 割引率

# 参考文献

[1] Riedmiller, M. (2005). Neural Fitted Q Iteration – First Experiences with a Data Efficient Neural Reinforcement Learning Method. In: Gama, J., Camacho, R., Brazdil, P.B., Jorge, A.M., Torgo, L. (eds) Machine Learning: ECML 2005. ECML 2005. Lecture Notes in Computer Science(), vol 3720. Springer, Berlin, Heidelberg. https://doi.org/10.1007/11564096_32
