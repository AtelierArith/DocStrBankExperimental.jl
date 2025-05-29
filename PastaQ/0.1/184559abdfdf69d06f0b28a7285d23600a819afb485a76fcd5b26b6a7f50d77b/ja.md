```
fidelity(A::MPO, B::MPO; process::Bool = false, cutoff::Float64 = 1e-15)
```

2つのMPO $A$と$B$の間のフィデリティ $F$。以下を実装します：

1. $$
    A
    $$

    と$B$が密度演算子である場合、$F$は完全な量子状態のフィデリティです。

$$
F(\rho,\sigma) = \Big(\text{Tr}\sqrt{\sqrt{\rho}\sigma\sqrt{\rho}}\Big)^2.
$$

注意：これは、完全な対角化を含むため、量子ビットの数$n$に対して指数関数的にスケールします。

2. $$
    A
    $$

    と$B$がユニタリ演算子（すなわちランク1チャネル）であり、`process = true`の場合、

$$
F
$$

はプロセスフィデリティです。

$$
F = 2^{-2n} \text{Tr}(A^\dagger B) = 2^{-2n} |\langle\Phi_A|\Phi_B\rangle|^2,
$$

ここで、$|\Phi_j\rangle = |j\rangle\rangle$はユニタリ演算子のベクトル化に対応するMPSです。

3. $$
    A
    $$

    がチョイ行列で、`B`がユニタリ演算子（またはその逆）の場合、プロセスフィデリティを返します。

$$
F = 2^{-2n} \text{Tr}(A |\Phi_B\rangle\langle\Phi_B|) = \langle\Phi_B|A|\Phi_B\rangle.
$$

4. $$
    A
    $$

    と$B$が両方ともチョイ行列である場合、完全なプロセスフィデリティを返します。

$$
F(A,B) = 2^{-2n}\Big(\text{Tr}\sqrt{\sqrt{A}B\sqrt{A}}\Big)^2.
$$

これは、上記のように、$n$に対して指数関数的にスケールします。
