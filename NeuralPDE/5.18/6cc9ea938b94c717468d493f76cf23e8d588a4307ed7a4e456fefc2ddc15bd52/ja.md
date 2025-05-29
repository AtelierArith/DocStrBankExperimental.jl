BPINNソリューションには、AdvancedHMC.jlサンプリングからの元のソリューションが含まれています（BPINNstatsにはそれに関連するフィールドがあります）。

1. `ensemblesol` は、すべてのサンプリングされたパラメータを使用して作成されたすべてのニューラルネットワークの出力からのアンサンブルソリューションの確率的推定（MonteCarloMeasurements.jl Particlesタイプ）です。
2. `estimated_nn_params` - サンプリングされた重み、バイアスからのNNパラメータの確率的推定です。
3. `estimated_de_params` - サンプリングされた未知のDEパラメータからのDEパラメータの確率的推定です。
