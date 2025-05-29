```
covariance_game([rng=GLOBAL_RNG], nums_actions, rho)
```

N人以上のプレイヤーのランダムなNormalFormGameインスタンスを返します。ここで、報酬プロファイルは、任意のペアの報酬の共分散が`rho`に等しい標準多変量正規分布から独立に引き出されます。これはRinottとScarsini（2000）で研究されています。

# 引数

  * `rng::AbstractRNG=GLOBAL_RNG`: 使用される乱数生成器。
  * `nums_actions::NTuple{N,Int}`: 各プレイヤーのアクション数のタプル。
  * `rho::Real`: ペアの報酬値の共分散。Nはプレイヤーの数であり、[-1/(N-1), 1]の範囲内でなければなりません。

# 戻り値

  * `::NormalFormGame`: 生成されたランダムなN人プレイヤーのNormalFormGame。

# 例

```julia
julia> using GameTheory, Random

julia> rng = MersenneTwister(12345);

julia> g = covariance_game(rng, (4, 3), -0.7);

julia> println(g)
4×3 NormalFormGame{2, Float64}:
 [1.17236, -0.211696]   [1.46647, -1.13947]    [0.378353, 0.603951]
 [0.415565, 0.0779055]  [0.606808, 1.00812]    [1.12871, -1.03399]
 [0.685759, -0.278449]  [-0.588508, 0.464548]  [-0.970332, -0.0319236]
 [-1.47708, 1.12447]    [1.92585, -2.27959]    [-2.1476, 1.53569]
```

# 参考文献

  * Y. Rinott and M. Scarsini, "On the Number of Pure Strategy Nash Equilibria in Random Games," Games and Economic Behavior (2000), 274-293.
