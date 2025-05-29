```
optimizer(x0, params)
```

最適化問題によってパラメータ化された `params` に従って、`x0` から始まる最適な軌道を生成します。この呼び出しは `params` に対して微分可能です。

この関数の出力は `(; xs, us, λs)` の形式で配置されており、

  * `xs::Vector{<:Vector}`: ベクトル値の状態の時間にわたるベクトル。
  * `us::Vector{<:Vector}`: ベクトル値の入力の時間にわたるベクトル。
  * `λ::Vector`: スカラー不等式制約の乗数のベクトル。私たちの符号規約により、すべての不等式双対は非負です。
  * `info::NamedTuple`: 追加の「低レベル」情報。!!この info 出力フィールドは微分可能ではないことに注意してください！

# 例

```@example running_example
x0 = zeros(4)
params = zeros(20)
solution = optimizer(x0, params)
```
