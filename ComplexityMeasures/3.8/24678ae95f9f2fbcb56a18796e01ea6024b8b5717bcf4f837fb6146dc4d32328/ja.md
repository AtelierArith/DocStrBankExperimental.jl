```
RelativeAmount <: ProbabilitiesEstimator
RelativeAmount()
```

`RelativeAmount`推定器は、最大尤度推定（MLE）を使用して、与えられた[`OutcomeSpace`](@ref)に対する確率を推定するために[`probabilities`](@ref)および関連関数と共に使用されます。使用法については、[`ProbabilitiesEstimator`](@ref)を参照してください。

## 説明

長さ`m`の結果空間$\Omega$と長さ`N`のランダムサンプルを考えます。`k`-番目の結果$\omega_k$の確率の最大尤度推定は次のようになります。

$$
p(\omega_k) = \dfrac{n_k}{N},
$$

ここで、$n_k$は（エンコードされた）サンプル内で`k`-番目の結果が観測された回数です。

この推定は*最大尤度推定*として知られています。しかし、`RelativeAmount`は、カウントベースでない[`OutcomeSpace`](@ref)のフォールバック確率推定器としても機能し、「擬似カウント」のみを生成します。例えば、[`WaveletOverlap`](@ref)や[`PowerSpectrum`](@ref)などです。これらの結果空間はカウントを生成せず、「相対頻度」または「相対パワー」として扱うことができる事前正規化された数値を生成します。したがって、この推定器は`RelativeAmount`と呼ばれます。

## 例

```julia
using ComplexityMeasures
x = cumsum(randn(100))
ps = probabilities(OrdinalPatterns{3}(), x) # `RelativeAmount`はデフォルトの推定器です
ps_mle = probabilities(RelativeAmount(), OrdinalPatterns{3}(), x) # 同等
ps == ps_mle # true
```

関連情報: [`BayesianRegularization`](@ref), [`Shrinkage`](@ref).
