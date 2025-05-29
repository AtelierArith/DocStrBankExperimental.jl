```julia
    generalizedMean(𝐏::Union{ℍVector, 𝔻Vector}, p::Real;
    <
    w::Vector=[],
    ✓w=true,
    ⏩=true >)
```

正定行列の1d配列$𝐏={P_1,...,P_k}$（[ℍVector type](@ref)または実正定対角行列の[𝔻Vector type](@ref)）とオプションの非負実重みベクトル$w={w_1,...,w_k}$を与えると、実数パラメータ$p$を用いた*加重一般化平均* $G$を返します。すなわち、

$$
G=\big(\sum_{i=1}^{k}w_iP_i^p\big)^{1/p}
$$

。

*<optional keyword argument>* $w$で重みベクトルを渡さない場合、*無加重一般化平均*を返します。

$$
G=\big(\sum_{i=1}^{k}P_i^p\big)^{1/p}
$$

。

*<optional keyword argument>* `✓w=true`（デフォルト）の場合、重みは1になるように正規化されます。そうでない場合、渡された通りに使用され、すでに正規化されている必要があります。このオプションは、毎回重みを正規化することなくこの関数を繰り返し呼び出すことを可能にします。

*<optional key argmuent>* ⏩=trueの場合、一般化平均の計算はマルチスレッドで行われます。

!!! note "Nota Bene"
    [マルチスレッド](https://docs.julialang.org/en/v1/manual/parallel-computing/#Multi-Threading-(Experimental)-1)は、Juliaが1つのスレッドのみを使用するように指示された場合、自動的に無効になります。[Threads](@ref)を参照してください。


パラメータ$p$の以下の特別なケースは注目に値します：

  * $$
    p=\frac{1}{2}
    $$

    の場合、一般化平均は[修正バッタチャリヤ平均](@ref)です。
  * $$
    p=1
    $$

    の場合、一般化平均は[ユークリッド](@ref)平均です。
  * $$
    p=-1
    $$

    の場合、一般化平均は[逆ユークリッド](@ref)平均です。
  * $$
    p=0
    $$

    （その極限）の場合、一般化平均は[対数ユークリッド](@ref)平均であり、行列$𝐏$のすべてが対角的に可換であるときは[Fisher](@ref)平均になります。

行列$𝐏$のすべてが対角的に可換である場合、例えば行列が対角行列である場合、一般化平均は任意の$p∈[-1, 1]$に対して[冪平均](@ref)と一致し、$p=0.5$の場合は[ワッサースタイン](@ref)平均とも一致します。このため、一般化平均は[`powerMean`](@ref)および[`wasMean`](@ref)アルゴリズムのデフォルト初期化に使用されます。

**参照**: [一般化平均](@ref)。

**関連**: [`powerMean`](@ref), [`wasMean`](@ref), [`mean`](@ref)。

**例**

```julia
using LinearAlgebra, Statistics, PosDefManifold
# 4つのランダムな3x3 SPD行列のセットを生成
Pset=randP(3, 4) # または、ユニコードを使用して: 𝐏=randP(3, 4)

# 重みベクトル、正規化する必要はありません
weights=[1, 2, 3, 1]

# 無加重平均
G = generalizedMean(Pset, 0.25) # または: G = generalizedMean(𝐏, 0.25)

# 加重平均
G = generalizedMean(Pset, 0.5; w=weights)

# 以前に正規化された重みを使用する場合、✓w=falseを設定できます
weights=weights./sum(weights)
G = generalizedMean(Pset, 0.5; w=weights, ✓w=false)

# 行列の数が多い場合はマルチスレッドで実行
using BenchmarkTools
Pset=randP(20, 160)
@benchmark(generalizedMean(Pset; ⏩=false)) # シングルスレッド
@benchmark(generalizedMean(Pset)) # マルチスレッド
```
