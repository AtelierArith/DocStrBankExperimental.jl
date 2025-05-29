```
Metropolis{P,R<:AbstractRNG,C<:Function} <: AriannaAlgorithm
```

メトロポリスモンテカルロアルゴリズムを表す構造体です。

# フィールド

  * `pools::Vector{P}`: 独立したプールのベクター（各システム用）
  * `sweepstep::Int`: スイープごとのモンテカルロステップ数
  * `seed::Int`: ランダム数シード
  * `rngs::Vector{R}`: ランダム数生成器のベクター
  * `parallel::Bool`: 異なるスレッドで並列化するためのフラグ
  * `collecter::C`: 並列化されたループから結果を収集するためのトランスデューサ

# 型パラメータ

  * `P`: プールの型
  * `R`: ランダム数生成器の型
  * `C`: トランスデューサの型
