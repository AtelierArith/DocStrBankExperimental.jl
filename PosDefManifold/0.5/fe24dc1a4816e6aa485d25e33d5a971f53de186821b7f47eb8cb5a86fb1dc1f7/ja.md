```
(1) regularize!(P::ℍ; <SNR=10e3>)
(2) regularize!(𝐏::ℍVector; <SNR=10e3>)
```

いずれかに[ホワイトノイズ](https://bit.ly/2TN8472)を追加します。

  * (1) サイズ $n⋅n$ の正定値行列 $P$、または
  * (2) サイズ $n⋅n$ の $k$ 個の正定値行列の 1d 配列 $𝐏$、[ℍVector 型](@ref)。

追加されたノイズは、逆行列に関する行列の条件を改善します。これは、これらの行列を分解する際や、固有値の対数などのいくつかの関数を評価する際の数値エラーを回避するために使用されます。

定数値が (1) の $P$ または (2) の $𝐏$ のすべての行列の対角要素に追加されます。すなわち、出力として：

$$
\textrm{(1)}\hspace{2pt}P\leftarrow P+ηI
$$

$$
\textrm{(2)}\hspace{2pt}𝐏_i\leftarrow 𝐏_i+ηI, \hspace{2pt}\textrm{for}\hspace{2pt} i=1:k.
$$

追加されるノイズの量 $η$ は、デフォルトで 10000 の `SNR` *<キーワード引数>* によって決定されます。これは次のようになります。

$$
\textrm{(1)}\hspace{2pt}SNR=\frac{\displaystyle\textrm{tr}(P)}{\displaystyle\textrm{tr}(ηI)}.
$$

$$
\textrm{(2)}\hspace{2pt}SNR=\frac{\displaystyle\sum_{i=1}^{k}\textrm{tr}(𝐏_i)}{\displaystyle k\hspace{1pt}\textrm{tr}(ηI)}.
$$

(1) の $P$ はエルミートとしてフラグを立てる必要があります。[行列の型変換](@ref)を参照してください。

!!! note "Nota Bene"
    キーワード引数 `SNR` は SNR（[信号対雑音比](https://bit.ly/1VvpvnQ））を表し、デシベルではなく、SNR 分散比として表されます。正の数でなければなりません。関数 `randΛ`[`randEigvalsMat`](@ref)、`randλ`[`randEigvals`](@ref)、および `randP`[`randPosDefMat`](@ref) とは異なり、ここでの SNR は期待される SNR ではなく、実際の SNR です。


**関連情報**: `randP` ([`randPosDefMat`](@ref))。

**例**

```julia
# (1)
using LinearAlgebra, Plots, PosDefManifold
n=3
U=randU(n)
# Q には、正則化されていない行列と正則化された行列を並べて書きます
Q=Matrix{Float64}(undef, n, n*2)
P=ℍ(U*Diagonal(randn(n).^2)*U') # 実数の 3x3 正の行列を生成
for i=1:n, j=1:n Q[i, j]=P[i, j] end
regularize!(P, SNR=5)
for i=1:n, j=1:n Q[i, j+n]=P[i, j] end # 正則化された行列は右側にあります
heatmap(Matrix(Q), yflip=true, c=:bluesreds)

# (2)
𝐏=[ℍ(U*Diagonal(randn(3).^2)*U') for i=1:5] # 5 つの実数 3x3 正の行列
regularize!(𝐏, SNR=1000)

## テストを実行
using LinearAlgebra
𝐏=randP(10, 100, SNR=1000); # 100 の実数エルミート行列
signalVar=sum(tr(P) for P in 𝐏);
regularize!(𝐏, SNR=1000);
signalPlusNoiseVar=sum(tr(P) for P in 𝐏);
output_snr=signalVar/(signalPlusNoiseVar-signalVar)
# output_snr はおおよそ 1000 に等しいはずです
```
